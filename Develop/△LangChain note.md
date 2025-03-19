# LangChain
## 提示词工程
### 提示词
####  立角色
引导AI进入具体场景，赋予其行家身份
#### 述问题
告诉AI你的困惑和问题，以及背景信息
#### 定目标
告诉AI你的需求，希望达成的目标
#### 补要求
告诉AI回答时注意什么，或者如何回复

### 提示词模板
- 将提示词提炼成模板
- 实现提示词的复用、版本管理、动态变化等

### Prompts模板
#### PromptTemplate字符串模板
##### 语法
- 导包
```
from langchain.prompts import PromptTemplate
```
- 设定字符模板
```
prompt = PromptTemplate.from_temple("Give me a {country} name")
prompt.format(country='UK')
```

#### ChatPromptTemplate对话模板
##### 语法
- 导包
```
from langchain.prompts import ChatPromptTemplate
```
- 设定模板
```
prompt = ChatPromptTemplate.from_messages(
	[
		("system","You are a software engineer, your name is {name}."),
		("human","Hello {}, how are you?"),
		("ai","Hello, I am good"),
		("human","{user_input}"),
	]
)

prompt.format_messages(name="James", user_input="What is your name")
```

#### Message模板
##### SystemMessage模板
```
SystemMessage(
    content=""
)
```
##### HumanMessage模板
```
HumanMessage(
    content=""
)
```
##### AIMessage模板
```
AIMessage(
    content=""
)
```
#### StringPromptTemplate自定义模板
一般写一个类来继承StringPromptTemplate，然后在类中自定义功能

#### f-string模板
f-string是python内置的一种模板引擎
```
from langchain.prompts import PromptTemplate

fstring_template = """
Tell me a {what} strory about {name}
"""

prompt = PromptTemplate.from_template(ftring_template)
prompt.format(name="Dan", what="sad")
```

#### jinja2模板
jinji2是一个灵活高效的Python模板引擎，可以方便的生成各种标记格式的文档
```
pip install jinja2
```
```
from langchain.prompts import PromptTemplate

jinja2_template = "Tell me a {what} strory about {name}"
prompt = PromptTemplate.from_template(
jinja2_template, template_format='jinja2')

prompt.format(name="Dan", what="sad")
```
#### 组合模板
组合模板更灵活，更适合开发使用
##### API
- Final prompt
最终返回的提示词模板
```
from langchain.prompts.prompt import PromptTemplate
```

- Pipeline prompt
组成提示词管道的模板
```
from langchain.prompts.pipeline import PipelinePromptTemplate
```

##### 三层提示词设计
- 第1层--基本性格设计
- 第2层--描述行为和性格
- 第3层--不允许做的事情


### 使用文件管理提示词模板
#### 优点
- 便于共享
- 便于版本管理
- 便于存储
- 支持常见格式
  - json
  - yaml
  - txt

#### 语法
```
from langchain.prompts import load_prompt

prompt = load_prompt("prompt.json")
```


### 示例选择器
#### 根据长度要求智能选择示例
根据输入的提示词长度，综合计算最终长度，只能截取或添加提示词的实例
##### 导包
```
from langchain.prompts.example_selector import LengthBasedExampleSelector
```
##### 参数
```
example_selector = LengthBasedExampleSelector(
    examples = 
    examples_prompt = 
    max_length = 
)
```

#### 根据输入相似度选择示例----最大边际相关性（MMR）
通过相似度来选取样例中最接近的，从而缩短提示词长度
##### 概念
- MMR是一种在信息检索中常用的方法，它的目标是在相关性和多样性之间找到一个平衡
- MMR会首先找出与输入最相似（即余弦相似度最大）的样本
- 然后在迭代添加样本的过程中，对于与已选择样本过于接近（即相似度过高）的样本进行惩罚
- 关注如何在相关性和多样性之间找到平衡

##### 导包
```
from langchain.prompts import MaxMarginalRelevanceExampleSelector
```
##### 示例
```
from langchain.prompts import MaxMarginalRelevanceExampleSelector
from langchain_community.vectorstores import FAISS
from langchain_ollama import OllamaEmbeddings
from langchain.prompts import PromptTemplate
from langchain_core.prompts import FewShotPromptTemplate
from langchain_ollama import ChatOllama

model = ChatOllama(model='Llama3.2', base_url="http://localhost:11434",temperature=0, verbose=True)

embeddings = OllamaEmbeddings(
    model="llama3.2:latest",
    base_url="http://localhost:11434"
)


example_prompt = PromptTemplate(
    input_variables = ['input', 'output'],
    template = 'original: {input} \nantonym: {output}'
)

examples = [
    {'input':'big', 'output':'small'},
    {'input':'tall', 'output':'short'},
    {'input':'happy', 'output':'sad'},
    {'input':'friend', 'output':'enemy'}
]

example_selector = MaxMarginalRelevanceExampleSelector.from_examples(
    examples = examples,
    embeddings = embeddings,
    vectorstore_cls = FAISS,
    k=2
)

dynamic_prompt = FewShotPromptTemplate(
    example_selector=example_selector,
    example_prompt = example_prompt,
    prefix='Please give me the antonym of every input word using examples format',
    suffix='input: {word} \nantonym: ',
    input_variables=['word']
)

print(dynamic_prompt.format(word='old'))
```

#### 根据输入相似度选择示例----最大余弦相似度
通过相似度来选取样例中最接近的，从而缩短提示词长度
##### 概念
- 一种常见的相似度计算方法
- 通过计算两个向量（向量可以表示文本、句子或词语）之间的余弦值来衡量它们的相似度
- 余弦值越接近1，表示两个向量越相似
- 主要关注的是如何准确衡量两个向量的相似度
##### 导包
```
from langchain.prompts import SemanticSimilarityExampleSelector
```

## RAG
检索增强生成（Retrieval-Augmented Generation）
### 概念
- 为LLM提供来自外部知识源的额外信息的概念
- 这允许它们生成更准确和有上下文的答案，同时减少幻觉
### 核心步骤
- 检索
外部相似搜索
- 增强
提示词更新
- 生成
更详细的提示词输入LLM
### Langchain中的RAG实现
#### Data connection
- Source
- Load
- Transform
- Embed
- Store
- Retrieve
#### Data processing
- 各种文档
- 各种Loader
- 文本切片
- 嵌入向量化
- 向量储存
- 各种检索链


### Loader
#### 加载markdown
- 导包
```
from langchain_community.document_loaders import TextLoader
```

#### 加载csv
- 导包
```
from langchain_community.document_loaders import CSVLoader
```

#### 加载HTML
加载HTML中的有效信息
- 导包
```
from langchain_community.document_loaders import BSHTMLLoader
```

#### 加载JSON
- 导包
```
from langchain_community.document_loaders import JSONLoader
```
- 示例
```
json_loader = JSONLoader('sample_data.json', jq_schema='.users', text_content=False)
print(json_loader.load())
print('-' * 20)
```
jq_schema是显示JSON中的哪个字段，.+字段名

#### 加载PDF
- 导包
```
from langchain_community.document_loaders import PyPDFLoader
```
- 功能
  - 把PDF文件分页输出
```
loader.load_and_split()
```

### 文档转换
#### 文档切割器和按文字分割

#### 代码文档分割器

#### 按token分割文档

#### 文档总结、精炼、翻译





















































































































































