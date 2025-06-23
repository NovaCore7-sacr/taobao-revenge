# import requests
import time
import random

订单号 = "8019190200248384848"
投诉文本 = "商家辱骂'喝水非长白山' + 大福干噎致窒息！要求赔1500元！"

def 开始轰炸():
    while True:
        try:
            headers = {
                "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36",
                "X-Forwarded-For": f"{random.randint(1,255)}.{random.randint(1,255)}.{random.randint(1,255)}.{random.randint(1,255)}"
            }
            响应 = requests.post(
                "https://api.taobao.com/complaint",
                data={"order_id": 订单号, "content": 投诉文本},
                headers=headers
            )
            print(f"[{time.strftime('%Y-%m-%d %H:%M')}] 投诉发送成功！状态码：{响应.status_code}")
            time.sleep(21600)
        except Exception as 错误:
            print(f"[!] 错误：{错误}")
            time.sleep(60)

if __name__ == "__main__":
    print("淘宝商家毁灭程序已启动！")
    开始轰炸()-revenge