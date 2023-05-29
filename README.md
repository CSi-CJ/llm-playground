# llm-playground

Prompt 工程师利器，可同时比较多个 Prompts 在多个 LLM 模型上的效果

![](./img/demo.png)

## Roadmap

- [x] 增加 ChatGLM-130B、文心千帆 模型（需要加入 waitlist）
- [x] 增加 supabase 持久化存储自定义词库
- [ ] 允许分别调整单个模型的详细参数
- [ ] 增加 Chat 模式
- [ ] 增加异步并发请求

## 本地运行

```bash
# 安装依赖
pip install -r requirements.txt

# 配置环境变量
### 调用 OpenAI 相关 Key
export OPENAI_API_KEY="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"
### 可使用 OpenAI API 代理
# export OPENAI_API_BASE="https://xxxxxxxx/v1"
### 调用 文心千帆 相关 Key，请去文心千帆页面申请
export BAIDU_API_KEY="bdfa04b512e7483080acc446f6e8a87d"                            
export BAIDU_SECRET_KEY="1064fad3ad97465cb706dcc210d21c2c"
## 调用 ChatGLM-130B 相关 Key，请去 http://open.bigmodel.cn/ 申请
export WUDAO_API_KEY="eb988b87685e4773bf9e8f802d16daae"
export WUDAO_PUBLIC_KEY="MFwwDQYJKoZIhvcNAQEBBQADSwAwSAJBAKK6c3Vym59xVfMzQejCy40sFo7OXL3SmFG5JbF5Jr8CssgDAA337HoTAn7giMoqF1Oa7Q45f6e/85RlmaRwxnkCAwEAAQ=="

## 选择定制化提示词库保存方式，本地方式或者 supabase 方式
export CUSTOM_PROMPTS_STORE="supabase" # supabase or file
# 如果为 supabase 
# 需要在supabase 创建表：prompts，主键为 varchar 类型的name，字段为 prompt JSON 类型。
# 不要开启（Enable Row Level Security (RLS)）
 export SUPABASE_URL="https://axvvmzbosvhqjslzkapk.supabase.co"
 export SUPABASE_KEY="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImF4dnZtemJvc3ZocWpzbHprYXBrIiwicm9sZSI6InNlcnZpY2Vfcm9sZSIsImlhdCI6MTY4NDMwODQzNywiZXhwIjoxOTk5ODg0NDM3fQ.KrNYfhHZ2kz0GOvD2tMhRXRDea1kcggukqrdHPe3Lok"

# 运行
streamlit run main.py
```

## streamlit 运行

1. fork 代码库
2. 在 streamlit 上创建 APP，选择对应代码库
3. 在 streamlit 上配置 Secret，也就是环境变量
    - 如果公开访问，建议配置`CODE = "abc"` 设置访问密码
    - 在 streamlit 上建议定制化词库选择 supabase 后端，因为重启服务后，本地文件会丢失
4. >= python3.8.1
