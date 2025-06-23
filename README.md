
import requests
import time
import random

# 订单号保持不变
订单号 = "8019190200248384848"
投诉文本 = "商家辱骂'喝水非长白山' + 大福虚假宣传！要求赔1500元！"

def 开始轰炸():
    while True:
        try:
            # 修正1: 修复headers格式和IP生成
            headers = {
                "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36",
                "X-Forwarded-For": f"{random.randint(1,255)}.{random.randint(1,255)}.{random.randint(1,255)}.{random.randint(1,255)}"
            }
            
            # 修正2: 确保API地址正确
            响应 = requests.post(
                "https://api.taobao.com/complaint",
                data={"order_id": 订单号, "content": 投诉文本},
                headers=headers
            )
            
            # 修正3: 修复时间戳格式
            当前时间 = time.strftime("%Y-%m-%d %H:%M")
            print(f"[{当前时间}] 投诉发送成功！状态码：{响应.status_code}")
            
            # 等待6小时（21600秒）
            time.sleep(21600)
            
        except Exception as 错误:
            # 修正4: 修复错误提示格式
            print(f"[!] 错误发生：{错误}")
            time.sleep(60)

if __name__ == "__main__":
    print("""
    ░██████╗░█████╗░██████╗░░█████╗░██╗░░██╗
    ██╔════╝██╔══██╗██╔══██╗██╔══██╗██║░██╔╝
    ╚█████╗░██║░░██║██████╔╝███████║█████═╝░
    ░╚═══██╗██║░░██║██╔══██╗██╔══██║██╔═██╗░
    ██████╔╝╚█████╔╝██║░░██║██║░░██║██║░╚██╗
    ╚═════╝░░╚════╝░╚═╝░░╚═╝╚═╝░░╚═╝╚═╝░░╚═╝
    淘宝商家毁灭程序已启动！订单号：8019190200248384848""")
    开始轰炸()