## CEX 중앙화거래소 (은행 역할!!)
> 중앙화된 기관이 운영하는 가상자산 거래 플랫폼
>> 전통적인 증권거래소와 유사한 운영 방식
>> 예: Binance, Upbit, Bithumb, Coinbase 등

### 시스템 구조 (중앙화 거래소)
```mermaid
graph TB
    subgraph Client ["🌐 클라이언트 계층"]
        WEB["💻 웹 클라이언트"]
        MOB["📱 모바일 앱"]
        API["🔌 API 클라이언트"]
    end

    subgraph Security ["🔐 보안 계층"]
        WAF["🛡️ WAF"]
        DDOS["🚫 DDoS 방어"]
        SSL["🔒 SSL/TLS"]
    end

    subgraph Gateway ["🚪 게이트웨이 계층"]
        NGINX["⚡ NGINX"]
        LB["⚖️ 로드밸런서"]
        API_GW["🌐 API Gateway"]
    end

    subgraph Service ["💼 서비스 계층"]
        direction TB
        subgraph Trading ["거래 관련 서비스"]
            ME["💱 매칭 엔진"]
            OS["📊 주문 시스템"]
            MP["💰 마켓 프라이스"]
        end
        
        subgraph Account ["계정 관련 서비스"]
            AUTH["🔑 인증 서비스"]
            KYC["👤 KYC/AML"]
            WLT["👛 지갑 관리"]
        end
        
        subgraph Support ["부가 서비스"]
            CS["💁 고객지원"]
            NOTI["📨 알림"]
            RPT["📈 리포팅"]
        end
    end

    subgraph Data ["💾 데이터 계층"]
        direction TB
        REDIS["⚡ Redis"]
        KAFKA["📨 Kafka"]
        DB[("🗄️ DB Cluster")]
        TS[("📊 시계열 DB")]
    end

    subgraph External ["🌍 외부 시스템"]
        BC["⛓️ 블록체인 노드"]
        SMS["📱 SMS 서비스"]
        EMAIL["📧 이메일"]
        BANK["🏦 은행"]
    end

    %% 연결
    Client --> Security
    Security --> Gateway
    Gateway --> Service
    Service --> Data
    Service --> External
    Trading --> Data
    Account --> Data
    Support --> Data

    %% 스타일
    classDef default fill:#f9f9f9,stroke:#333,stroke-width:1px
    classDef service fill:#ddf,stroke:#333,stroke-width:1px
    classDef data fill:#dfd,stroke:#333,stroke-width:1px
    classDef external fill:#fdd,stroke:#333,stroke-width:1px
    
    class Trading,Account,Support service
    class Data data
    class External external
```

### 1. 주요 특징
```
주문장(Order Book) 기반 거래
실시간 매수/매도 매칭
시장가/지정가 주문 지원
레버리지 거래 제공
```

### 2. 보안
```
KYC(본인인증) 필수
AML(자금세탁방지) 규정 준수
고객 자산 중앙 관리
콜드월렛/핫월렛 분리 운영
```

### 3. 장점
```
높은 거래 속도와 처리량
유동성 풍부
고객 지원 서비스 제공
분실 시 계정 복구 가능
사용자 친화적 인터페이스
```

### 4. 단점
```
중앙 기관에 대한 의존성
해킹 위험 존재
거래소 규정에 따른 제약
수수료 구조가 다소 높음
```

### 5. 💰수익 구조 (수수료)
```
거래 수수료 수입
입출금 수수료
토큰 상장 수수료
레버리지 거래 수수료
기타 부가 서비스 수익
```
