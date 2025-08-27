import os
from langchain_community.chat_models.tongyi import ChatTongyi
from langchain.schema import HumanMessage, SystemMessage

# 创建 LangChain 的 ChatOpenAI 实例
llm = ChatTongyi(
    model="qwen-plus",  # 有效模型名（qwen-turbo/qwen-plus/qwen-max）
    api_key=os.getenv("DASHSCOPE_API_KEY"),  # 从环境变量读取密钥
    temperature=0.7,  # 回答灵活度（0-1）
)
# 构建消息
messages = [
    SystemMessage(content="You are a helpful assistant."),
    HumanMessage(content="你是谁？"),
]

# 调用模型
response = llm.invoke(messages)

# 输出结果
print(response.content)
