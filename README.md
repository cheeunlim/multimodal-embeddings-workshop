# **Gemini Embedding 2 및 Vector Search 2.0을 이용한 멀티모달 미디어 검색**

이 프로젝트는 Google Cloud에서 Gemini Embedding 2와 Vertex AI Vector Search 2.0을 사용하여 최첨단 멀티모달 검색 시스템을 구축하는 방법을 보여줍니다. 이미지와 장편 동영상을 포함한 혼합 미디어 유형을 처리하도록 설계되었으며, 멀티모달 시맨틱 검색을 가능하게 합니다.

## **실습 실행을 위한 Git Clone**

해당 레포지토리를 클론하거나, Colab Enterprise에 [실습 노트북](https://github.com/cheeunlim/multimodal-embeddings-workshop/blob/main/multimodal_search.ipynb)을 import 해서 사용하세요:

```bash
git clone https://github.com/cheeunlim/multimodal-embeddings-workshop.git
```

## **워크플로우 개요 및 아키텍처**

이 프로젝트는 환경 설정부터 고급 하이브리드 검색 구현까지 안내하는 6개의 주요 단계로 구성되어 있습니다.

### **1단계: 환경 설정 및 초기화**
프로젝트 ID, 리전, 워커 수, GCS 버킷 이름을 포함하여 필요한 환경 변수와 상수를 구성합니다. 이 단계에서는 Google Cloud 서비스와 상호 작용하기 위한 모든 전제 조건이 충족되었는지 확인합니다.

### **2단계: 데이터 로드 및 파일 목록 생성**
지정된 Google Cloud Storage(GCS) 버킷에서 파일 목록을 검색하고 이미지와 동영상으로 분류합니다. 이 동적 접근 방식은 정적 데이터 세트 레지스트리를 대체합니다.

### **3단계: 임베딩 추출 및 동영상 처리**
*   **동영상 청킹(Chunking)**: 대용량 동영상 파일은 세부적인 검색 및 정확한 타임스탬프 탐색을 가능하게 하기 위해 더 작고 관리하기 쉬운 청크(예: 30초)로 분할됩니다.
*   **병렬 처리**: `ThreadPoolExecutor`를 사용하여 동영상 청크와 이미지 모두에 대한 임베딩 추출을 병렬화하여 프로세스 속도를 크게 향상시킵니다.
*   **Gemini Embedding 2**: 최신 Gemini Embedding 모델을 활용하여 미디어 콘텐츠의 시맨틱 본질을 포착하는 고차원 밀집 벡터를 생성합니다.

### **4단계: Vector Search 2.0 설정**
Vertex AI Vector Search 2.0을 위한 서비스 클라이언트를 초기화하고 데이터 스키마를 정의합니다. 이 설정을 통해 미디어 임베딩을 메타데이터와 함께 관리형 검색 인덱스에 저장할 수 있습니다.

### **5단계: 미디어 검색 및 렌더링**
검색 기능과 렌더링 유틸리티를 정의하여 결과를 시각화합니다. 이 단계를 통해 인덱스를 쿼리하고 일치하는 이미지나 동영상 청크가 노트북에 직접 표시되는 것을 확인할 수 있습니다.

### **6단계: 고급 검색 (하이브리드 및 희소 벡터)**
Gemini의 밀집 벡터와 자연어 설명에서 생성된 희소 벡터(예: BM25)를 결합하여 하이브리드 검색을 구현합니다. 이 접근 방식은 시맨틱 의미와 특정 키워드를 모두 캡처하여 검색 정확도를 높입니다.

---

## **주요 기술**

*   **Google Gemini 모델**: 멀티모달 임베딩 생성 및 자연어 이해용.
*   **Vertex AI Vector Search 2.0**: 확장 가능하고 대기 시간이 짧은 벡터 유사성 검색용.
*   **MoviePy**: 동영상 처리 및 청킹용.
*   **Google Cloud Storage**: 소스 미디어 파일 저장용.

## **사용 방법**

1.  **노트북 열기**: `multimodal_search.ipynb`를 엽니다.
2.  **환경 구성**: Cell 2에서 `PROJECT_ID`와 `source_bucket_name`을 업데이트합니다.
3.  **셀 실행**: 셀을 순차적으로 실행하여 데이터를 처리하고 임베딩을 인덱싱하고 검색을 수행합니다.

> [!NOTE]
> 이 노트북은 일부 구성에서 수동 인덱스 배포 없이 직접 데이터 개체 관리 및 검색을 지원하는 베타 버전(`v1beta`)의 Vertex AI Vector Search 2.0을 사용합니다.

---
# **English Version**
---

# **Multimodal Media Search with Gemini Embedding 2 and Vector Search 2.0**

This project demonstrates how to build a state-of-the-art multimodal retrieval system using Gemini Embedding 2 and Vertex AI Vector Search 2.0 on Google Cloud. It is designed to handle mixed media types, including images and long-form videos, enabling semantic search across different modalities.

## **Git Clone for this Practice**

Clone this repository, or import the [practice notebook file](https://github.com/cheeunlim/multimodal-embeddings-workshop/blob/main/multimodal_search.ipynb) to Colab Enterprise to use it:

```bash
git clone https://github.com/cheeunlim/multimodal-embeddings-workshop.git
```

## **Workflow Overview & Architecture**

The project is structured into 6 main phases, guiding you from environment setup to advanced hybrid search implementation.

### **Phase 1: Environment Setup & Initialization**
Configure necessary environment variables and constants, including Project ID, Region, worker counts, and GCS bucket names. This phase ensures all prerequisites are met for interacting with Google Cloud services.

### **Phase 2: Data Loading & File List Generation**
Retrieve the list of files from the specified Google Cloud Storage (GCS) bucket and classify them into images and videos. This dynamic approach replaces static dataset registries.

### **Phase 3: Embedding Extraction & Video Processing**
*   **Video Chunking**: Large video files are segmented into smaller, manageable chunks (e.g., 30 seconds) to allow for granular retrieval and precise timestamp seeking.
*   **Parallel Processing**: Utilizes `ThreadPoolExecutor` to parallelize embedding extraction for both video chunks and images, significantly speeding up the process.
*   **Gemini Embedding 2**: Leverages the latest Gemini Embedding model to generate high-dimensional dense vectors capturing the semantic essence of the media content.

### **Phase 4: Vector Search 2.0 Setup**
Initialize service clients for Vertex AI Vector Search 2.0 and define the data schema. This setup enables storing media embeddings along with metadata in a managed search index.

### **Phase 5: Media Search & Rendering**
Define search functions and rendering utilities to visualize the results. This phase allows you to query the index and see the matching images or video chunks displayed directly in the notebook.

### **Phase 6: Advanced Search (Hybrid & Sparse Vectors)**
Implement hybrid search by combining dense vectors from Gemini with sparse vectors (e.g., BM25) generated from natural language descriptions. This approach enhances search accuracy by capturing both semantic meaning and specific keywords.

---

## **Key Technologies**

*   **Google Gemini Models**: For multimodal embedding generation and natural language understanding.
*   **Vertex AI Vector Search 2.0**: For scalable, low-latency vector similarity search.
*   **MoviePy**: For video processing and chunking.
*   **Google Cloud Storage**: For storing source media files.

## **How to Use**

1.  **Open Notebook**: Open `multimodal_search.ipynb`.
2.  **Configure Environment**: Update the `PROJECT_ID` and `source_bucket_name` in Cell 2.
3.  **Run Cells**: Execute the cells sequentially to process data, index embeddings, and perform searches.

> [!NOTE]
> This notebook uses Vertex AI Vector Search 2.0 in beta (`v1beta`), which supports direct data object management and search without manual index deployment in some configurations.
