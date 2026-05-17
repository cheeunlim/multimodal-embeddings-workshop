# 워크숍 슬라이드 구성안 (완전 일치화)

이 문서는 `slides_to_.txt`의 번호 체계와 100% 일치하도록 개편된 슬라이드 구성안입니다.

---

#### Slide 1: Title Slide
*   **Title**: Gemini Embedding 2 & Vector Search
엔터프라이즈 멀티모달 검색 시스템 구축
*   **Content**:
    *   **Visual**: Text/Image/Video -> Gemini Embedding 2 -> Unified Space -> Vector Search 2.0
    *   **Text**: 차세대 AI 인프라를 활용한 기술 구현 가이드

---

#### Slide 2: 목차
*   **Title**: 목차
*   **Content**:
    *   멀티모달 검색의 발전
    *   Gemini Embedding 2
    *   Vector Search 2.0
    *   멀티모달 검색 활용 사례
    *   실습 내용 안내

---

#### Slide 3: Part 1: 멀티모달 검색의 발전
*   **Title**: 01 멀티모달 검색의 발전
*   **Content**:
    *   멀티미디어 콘텐츠의 진화와 검색의 과제

---

#### Slide 4: 멀티미디어 컨텐츠 발전
*   **Title**: 데이터의 진화와 검색의 과제
*   **Content**:
    *   기업 데이터의 다양화: 텍스트(PDF), 이미지, 비디오, 오디오 등
    *   데이터 규모의 방대한 증가로 인한 콘텐츠 발견(Discovery)의 어려움

---

#### Slide 5: 현재 솔루션의 문제점
*   **Title**: 기존 검색 방식의 한계
*   **Content**:
    *   **인간의 기억력 의존**: 전문가에 대한 높은 의존도
    *   **수동 태깅 (Human Labeling)**: 정보 손실 및 높은 인건비, 정의된 태그에 국한됨
    *   **ML 기반 라벨링**: 키워드 기반으로 너무 포괄적이고 노이즈가 많음

---

#### Slide 6: ML Tagging vs. Search
*   **Title**: ML Tagging vs. Search
*   **Content**:
    *   **ML Tagging**: 키워드 기반으로 너무 포괄적이고 노이즈가 많음 (예: "Person, green, landscape")
    *   **Search**: 사용자의 의도를 더 잘 이해하여 정확한 결과 제공 (예: "a person putting on the green")

---

#### Slide 7: What are Embeddings?
*   **Title**: 임베딩(Embedding)의 개념
*   **Content**:
    *   **개념**: 비정형 데이터(텍스트, 이미지 등)를 부동소수점 형태의 벡터로 변환하는 것
    *   **원리**: 의미론적 유사성(Semantic Similarity)을 다차원 공간의 거리로 정량화
    *   **생성**: 딥러닝 모델을 통해 데이터의 특징(Feature)을 추출하여 고차원 공간에 매핑

---

#### Slide 8: 멀티모달 임베딩의 필요성
*   **Title**: 멀티모달 임베딩의 필요성
*   **Content**:
    *   **이미지 및 비디오 검색**: 이종 데이터 규격간 유사 미디어의 멀티모달 검색
        *   데이터 규격 호환성 확보
        *   유사 미디어 자동 매칭
        *   멀티모달 검색 아키텍처
    *   **순위 및 추천**: 고객에게 적합한 광고 및 콘텐츠 추천
        *   Zero-shot 분류 수행
        *   얼굴 인식 및 분석
        *   이미지/비디오 풀 최적화
    *   **콘텐츠 적합성**: 부적절한 이미지, 비디오 또는 텍스트를 실시간 식별
        *   유해 콘텐츠 필터링
        *   텍스트/비주얼 통합 분석
        *   자동화된 모니터링

---

#### Slide 9: Multimodal 임베딩의 난제
*   **Title**: 멀티모달 검색의 난제
*   **Content**:
    *   이종 데이터(Text vs Image) 간의 벡터 공간 불일치
    *   단순히 텍스트로 변환(Captioning)할 경우 발생하는 정보의 왜곡과 손실

---

#### Slide 10: Part 2: Gemini Embedding 2
*   **Title**: 02 멀티모달 임베딩: Gemini Embedding 2
*   **Content**:
    *   차세대 네이티브 멀티모달 임베딩 모델 소개

---

#### Slide 11: Gemini Embedding 2 모델의 등장
*   **Title**: 차세대 네이티브 멀티모달 임베딩
*   **Content**:
    *   Google의 최초 다국어 멀티모달 임베딩 모델
    *   데이터를 다른 형태로 변환하지 않고 있는 그대로 이해 (Native Understanding)

---

#### Slide 12: Composite 벡터의 구성
*   **Title**: Gemini Embedding 2: Multimodal Input to Single Composite Vector
*   **Content**:
    *   1개의 Composite 벡터는 다음으로 구성 가능:
        *   최대 6개의 이미지
        *   최대 1개의 문서 (최대 6페이지)
        *   최대 1개의 동영상 (1FPS 영상만 이용 시 120초, 음성 포함 시 80초)
        *   최대 1개의 오디오 (180초)

---

#### Slide 13: 모델 스펙 설명
*   **Title**: Gemini Embedding 2 지원 규격
*   **Content**:
    *   **Text**: 최대 8,192 토큰
    *   **Image**: 요청당 최대 6개
    *   **Video**: 최대 120초 (오디오 포함 시 80초)
    *   **Audio**: 최대 180초
    *   **Output**: 최대 3,072 차원

---

#### Slide 14: 모델 스펙 비교
*   **Title**: Model Comparison: Performance & Capabilities
*   **Content**:
    *   **Text**: 최대 8,192 입력 토큰 지원
    *   **Images**: 요청당 최대 6개 이미지 처리 (PNG, JPEG)
    *   **Videos**: MP4 및 MOV 형식에서 최대 120초 비디오 입력 지원
    *   **Audio**: 중간 텍스트 변환 없이 네이티브 오디오 수집
    *   **Documents**: 최대 6페이지 길이의 PDF 직접 임베딩

---

#### Slide 15: MRL 설명
*   **Title**: 효율적인 차원 관리: MRL
*   **Content**:
    *   **개념**: 하나의 임베딩 벡터가 여러 크기의 차원(예: 256, 768, 3072)을 모두 대변할 수 있도록 학습
    *   **장점**: 앞부분의 적은 차원만 잘라서 써도 의미가 크게 손실되지 않음 -> 레이턴시 및 스토리지 비용 획기적 절감

---

#### Slide 16: 비디오 임베딩의 난제
*   **Title**: 비디오 임베딩: 시간의 벽을 넘기
*   **Content**:
    *   **난제**: 이미지의 연속인 비디오에서 '시간적 흐름'과 동작의 의미를 어떻게 캡처할 것인가?
    *   **기법 발전**: VideoCoca (시간 정보 부족), VLM 방식 (프레임별 평균)
    *   **Gemini의 해결책**: 프레임 간의 관계와 시간적 맥락을 네이티브하게 이해하여 Early Fusion 구현

---

#### Slide 17: 벡터 검색 구분 슬라이드
*   **Title**: 03 벡터 검색: Vector Search 2.0
*   **Content**:
    *   벡터 검색의 개념과 Vector Search 2.0 소개

---

#### Slide 18: 벡터 검색의 과제
*   **Title**: 대규모 벡터 검색의 도전 과제
*   **Content**:
    *   **난제**: 빠르고 확장 가능한 벡터 검색은 쉽지 않음
    *   **Brute Force Search**: O(dimensions x items)로 계산량 폭증 (예: 10M 벡터 검색 시 70억 번 연산 필요)

---

#### Slide 19: ANN과 ScaNN
*   **Title**: 대규모 벡터 검색의 해법: ANN & ScaNN
*   **Content**:
    *   **ANN (Approximate Nearest Neighbor)**: 모든 벡터를 전수 조사하지 않고, 근사치를 빠르게 찾는 알고리즘
    *   **ScaNN**: 구글이 2020년에 발표한 ANN 라이브러리 기반, 고속 정밀 검색 지원
    *   **활용**: Google Search, Play, YouTube 등 핵심 서비스 파워링

---

#### Slide 20: TL;DR: Why Vector Search 2.0
*   **Title**: 에이전트 검색을 위한 핵심 기능 요약 (TL;DR)
*   **Content**:
    *   **Easy to Use**: 직관적인 클라이언트 라이브러리로 몇 분 만에 시작 가능
    *   **Zero Infra Management**: 자동 확장 및 튜닝되는 자율형 엔진으로 앱 로직에만 집중
    *   **Fast Onboarding**: 즉시 컬렉션 생성, 데이터 추가 및 검색 가능
    *   **Unified Knowledge Core**: 벡터와 원본 데이터를 한 곳에 저장하고 강력한 필터링 지원
    *   **Powerful Reasoning**: 하이브리드 검색, 멀티 벡터 쿼리 등 강력하고 유연한 추론 지원
    *   **Adaptable & Scalable**: 프로토타입에서 프로덕션 규모까지 유연한 가격 및 성능 티어 제공

---

#### Slide 21: Best-in-class relevance
*   **Title**: 에이전트 시대를 위한 최고 수준의 관련성
*   **Content**:
    *   **통합 검색 파이프라인**: 데이터 및 쿼리 임베딩을 플랫폼이 직접 처리 (Auto-Embeddings)
    *   **하이브리드 검색 통합**: 다중 벡터 및 텍스트 검색을 병렬 실행하고 내장 랭커로 통합 리스트 생성
    *   **내장 랭커 (Semantic Ranker & RRF)**: 가중치 조절이 가능한 RRF로 이종 벡터 결과를 서버 사이드에서 자동 병합
    *   **멀티 벡터 지원**: 단일 데이터 객체에 여러 벡터 필드(예: 제목, 줄거리 등) 지원
    *   **미래 비전 (Self-Improving Agent)**:
        *   데이터 정제 및 청킹을 위한 커스텀 로직 주입 가능 (Programmable Pipeline)
        *   사용자 신호(클릭, 전환 등)를 학습하여 랭킹 로직 자동 개선 (Learn-to-rank)
        *   A/B 테스트를 위한 네이티브 실험 프레임워크 제공

---

#### Slide 22: Focus on your app, not infrastructure
*   **Title**: 인프라가 아닌 애플리케이션에 집중하세요
*   **Content**:
    *   **완전 관리형 자동 튜닝 엔진**: 성능 튜닝을 위한 수동 작업과 시행착오(Guesswork) 제거
    *   **초고속, 고확장성**: 수십억 규모의 데이터에서도 10ms 이하의 지연 시간(Sub-10ms)
    *   **인프라 추상화**: VM 선택이나 샤드(Shard) 구성 불필요, 복제본(Replica) 수동 정의 불필요
    *   **자동 성능 튜닝**: 애플리케이션 규모가 커져도 성능 유지를 위해 내부적으로 자동 튜닝 수행
    *   **안정적인 확장**: 프로토타입에서 대규모 운영 환경까지 원활하고 안정적인 스케일링 지원

---

#### Slide 23: Core concept: working with Collections
*   **Title**: 핵심 개념: Collection (Vector + Data 통합)
*   **Content**:
    *   **Collection**: 작업의 기본 리소스로, 관계형 DB의 테이블과 유사한 역할
    *   **컨테이너**: 연관된 JSON 데이터 객체들의 집합을 보유
    *   **유연한 스키마**: 데이터 구조를 정의하는 유연한 JSON 스키마 활용
    *   **통합 데이터 소스**: 벡터(Vector)와 원본 데이터(Payload)를 한 곳에 함께 저장하여 관리 효율성 극대화

---

#### Slide 25: 비디오 검색의 난제 (Crowding)
*   **Title**: 비디오 검색 최적화 전략
*   **Content**:
    *   **난제**: 긴 비디오에서 유사한 장면이 반복되어 검색 결과를 독점하는 문제 (Crowding)
    *   **전략**:
        *   **Logical Pacing**: 10~30초 단위의 의미 단위 청킹
        *   **Native Hybrid Ranking**: Vector Search 2.0의 내장 RRF를 통한 자동 순위 병합
        *   **Diversity Filter**: 특정 비디오의 과도한 노출을 막기 위한 애플리케이션 레벨의 후처리(필터링)

---

#### Slide 26: 하이브리드 검색 (Dense + Sparse)
*   **Title**: Dense + Sparse 하이브리드 검색
*   **Content**:
    *   **Dense (Gemini)**: 의미론적, 시각적 맥락 검색
    *   **Sparse (BM25)**: 고유명사, 품번 등 정확한 키워드 검색
    *   **자동화된 랭킹 (Reranker)**: Vector Search 2.0은 RRF(Reciprocal Rank Fusion)를 내장하여, 별도의 Reranker 구축 없이 서버 사이드에서 최적의 하이브리드 결과를 제공

---

#### Slide 27: Part 3: 멀티모달 검색 활용 사례
*   **Title**: 03 멀티모달 검색 활용 사례
*   **Content**:
    *   산업별 및 고객 성공 사례

---

#### Slide 28: 활용 사례 (군집 기반 이상 탐지 등)
*   **Title**: 군집 기반 이상 탐지 및 분석
*   **Content**:
    *   **방법 1: 군집 기반 이상 탐지**
        *   정상 군집의 센터로이드와 새로운 데이터의 거리가 평균 이상을 넘으면 비정상으로 판단
    *   **방법 2: 유사 이미지 비율 분석**
        *   잘린 사진 하나하나와 유사하게 생긴 이미지 중 25개의 유사한 이미지의 분류 비율로 병충해 판단

---

#### Slide 29: 리테일 케이스 1
*   **Title**: 상품 비주얼 기반 검색 (유사 스타일 찾기)
*   **Content**:
    *   텍스트로 설명하기 어려운 상품의 스타일, 패턴, 질감을 기반으로 유사 상품 검색

---

#### Slide 30: 리테일 케이스 2
*   **Title**: 이미지 + 텍스트 결합 검색
*   **Content**:
    *   특정 이미지에 텍스트 조건(예: "이 가방과 비슷하지만 가죽 재질인 것")을 추가하여 정밀 검색

---

#### Slide 31: 고객 성공 사례 (eBay, FOX Sports)
*   **Title**: 글로벌 기업의 활용 사례
*   **Content**:
    *   **eBay**: 이미지 기반 유사 상품 검색으로 쇼핑 경험 개선
    *   **FOX Sports**: 방대한 비디오 아카이브에서 특정 장면을 신속하게 검색 및 활용

---

#### Slide 32: 요약
*   **Title**: 요약: 멀티모달 검색의 3대 핵심 기둥
*   **Content**:
    *   **1. Gemini Embedding 2**: Native Multimodal 이해
    *   **2. Vector Search 2.0**: 확장 가능하고 강력한 검색 인프라
    *   **3. Hybrid Strategy**: 품질과 비용의 균형

---

#### Slide 33: 실습 안내 (구분 슬라이드)
*   **Title**: 04 실습 안내
*   **Content**:
    *   핸즈온 실습 환경 및 아키텍처 소개

---

#### Slide 34: 실습 구성 요소 아키텍처
*   **Title**: 실습 아키텍처 및 기술 스택
*   **Content**:
    *   **사용 기술**: Gemini Embedding 2, SimpleBM25, Vertex AI Vector Search 2.0
    *   **아키텍처 구조도**:
        ```mermaid
        graph LR
            subgraph Data_Ingestion["Data Ingestion & Processing"]
                GCS[("Google Cloud Storage<br>(원본 이미지 & 비디오)")]
                Chunking["비디오 분할<br>(MoviePy)"]
                Gemini_Embed["Gemini Embedding 2<br>(멀티모달 벡터 생성)"]
                
                GCS --> Chunking
                GCS --> Gemini_Embed
                Chunking --> Gemini_Embed
            end

            subgraph Storage_and_Search["Storage & Search Infrastructure"]
                VS2[("Vertex AI Vector Search 2.0")]
                Collection["Collection (스키마 정의)<br>- Dense 벡터 (이미지/비디오)<br>- Sparse 벡터 (텍스트)<br>- 메타데이터"]
                VS2 --- Collection
            end

            Gemini_Embed --> VS2

            subgraph Query_Flow["Query & Retrieval Flow"]
                Query["사용자 검색 쿼리<br>(텍스트 또는 이미지)"]
                Q_Embed["쿼리 벡터화<br>(Gemini Embedding 2)"]
                Results["검색 결과 병합<br>(Native RRF)"]
                UI["결과 시각화<br>(Notebook / Web UI)"]
                
                Query --> Q_Embed
                Q_Embed --> VS2
                VS2 --> Results
                Results --> UI
            end
        ```