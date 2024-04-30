동행복권 사이트에서 로또/연금복권을 구입하는 github action입니다.

프로그램 리파지토리: <https://github.com/chaeyk/lottery-agent>

# inputs

| 이름 | 설명 |
| --- | --- |
| username | 동행복권 사이트의 계정  |
| password | 동행복권 사이트 계정의 비밀번호 |
| telegram-bot-token | 텔레그램 봇ID. 없어도 됨 |
| telegram-chatid | 텔레그램 메시지 수신자 ID. 없어도 됨 |
| lo40 | 로또 구매 수량 |
| lp72 | 연금복권 구매 수량 |

# 예제

[사용중인 코드](https://github.com/chaeyk/lottery-agent/blob/main/.github/workflows/lottery_buy.yml)
  
```yaml
name: Lottery purchase

on:
  schedule:
  - cron: 00 10 * * 1 # every Monday on 07:00 PM (KST)
  workflow_dispatch: {}

jobs:
  check:
    runs-on: ubuntu-latest
    steps:
    - name: Check result
      uses: chaeyk/lottery-buy-action@v1
      with:
        username: ${{ secrets.DHL_USERID }}
        password: ${{ secrets.DHL_PASSWORD }}
        telegram-bot-token: ${{ secrets.TLG_BOTTOKEN }}
        telegram-chatid: ${{ secrets.TLG_CHATID }}
        lo40: ${{ vars.LO40_COUNT }}
        lp72: ${{ vars.LP72_COUNT }}
```
