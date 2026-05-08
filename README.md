# 🚀 한국석유관리원 EXAONE 3.5 SLM 모델 조사 보고서

본 보고서는 한국석유관리원 내부 업무 및 폐쇄망 환경에서 활용 가능한 Small Language Model(SLM)의 기술적 특성과 활용 가능성을 분석한 리포트입니다.

---

## 📊 분석 대상

| 항목 | 내용 |
| :--- | :--- |
| **모델** | EXAONE-3.5-2.4B-Instruct |
| **개발** | LG AI Research |
| **모델 유형** | Instruction-tuned Bilingual SLM |
| **파라미터** | 2.4B (실질 가중치 약 2.14B) |
| **컨텍스트 길이** | 32,768 Tokens |
| **아키텍처** | Decoder-only Transformer |
| **Attention** | GQA (Grouped Query Attention) |
| **토크나이저** | BBPE 기반 · Vocab 102,400 |
| **양자화 지원** | AWQ / GGUF |
| **라이선스** | EXAONE AI Model License 1.1-NC |

---

## 🔍 주요 분석 내용

### 1. 모델 선택 배경
* **한국어 성능 우수**: 동급 글로벌 모델 대비 한국어 이해 및 생성 능력이 뛰어남.
* **공공기관 폐쇄망 환경 적합**: 온프레미스 배포가 용이하여 보안성이 높음.
* **경량성**: 일반 사무용 PC 또는 보급형 GPU 환경에서도 구동 가능.
* **RAG 활용성**: 긴 컨텍스트 지원으로 법령 및 문서 검색 기반 시스템 구축에 유리.

### 2. 학습 및 튜닝 구조
* **사전학습**: 6.5T 토큰을 기반으로 학습되었으며, 한국어와 영어 비중이 50:50으로 구성됨.
* **정렬 튜닝**: SFT(Supervised Fine-Tuning)와 DPO, SimPO를 통한 인간 선호도 최적화 적용.
* **컨텍스트 확장**: 32K 토큰 처리를 위한 Long-context 확장 학습 완료.

### 3. 구조적 특징
* **Architecture**: 30-layer Decoder-only 구조를 채택.
* **Attention**: GQA(Grouped Query Attention)를 통해 추론 시 메모리 사용량 최적화.
* **Scaling**: RoPE Scaling을 적용하여 긴 문장에서도 일관된 성능 유지.

### 4. 모델 파일 구성
* `config.json`: 모델 설정 파일.
* `model.safetensors`: 실제 모델 가중치 파일.
* `tokenizer.json`: 토크나이저 정보.
* `generation_config.json`: 생성 관련 하이퍼파라미터 설정.
* `modeling_exaone.py`: 전용 아키텍처 구현 코드.

---

## 💼 활용 가능 업무 및 시나리오

### 활용 업무
* **법령 기반 RAG 질의응답**: 「석유사업법」 등 법령 및 고시 기반 지식 추출.
* **검사 규정 검색**: 내부 검사 매뉴얼 및 지침서 자동 검색 시스템.
* **업무 보조**: 문서 요약, 보고서 초안 생성 및 민원 응대 지원.

### 한국석유관리원 내부 법령 질의응답 시스템 시나리오
* EXAONE-3.5-2.4B-Instruct를 활용하여 보안이 확보된 폐쇄망 내 온프레미스 RAG 시스템 구축.
* 시행령·시행규칙 자동 검색 및 조문 근거에 기반한 신뢰도 높은 답변 생성.

---

## ⚡ 기술적 강점 요약

| 구분 | 특징 |
| :--- | :--- |
| **한국어 성능** | 동급 글로벌 모델 대비 우수 |
| **경량성** | GGUF 기준 1.5~2GB 수준으로 운영 가능 |
| **장문 처리** | 32K Context 지원으로 대용량 문서 분석 가능 |
| **배포 유연성** | Ollama / vLLM / llama.cpp 등 다양한 툴체인 지원 |

---

## ⚠️ 한계 및 주의사항
* **라이선스**: NC(비상업용) 라이선스이므로 실제 운영 시 라이선스 범위 확인 필요.
* **환각 현상**: LLM 특유의 사실 관계 오류 가능성이 존재하므로 인간의 검토 필수.
* **보안**: 커스텀 코드 실행을 위해 `trust_remote_code=True` 설정이 요구됨.

---

## 🔗 참고 링크
* [Hugging Face 모델 페이지](https://huggingface.co/LGAI-EXAONE/EXAONE-3.5-2.4B-Instruct)
* [EXAONE 공식 GitHub](https://github.com/LG-AI-EXAONE/EXAONE-3.5)
* [기술 보고서 (arXiv)](https://arxiv.org/abs/2412.04862)
* [Ollama 라이브러리](https://ollama.com/library/exaone3.5:2.4b)

---
**작성자:** 한국석유관리원_권용환
