한국석유관리원 EXAONE 3.5 SLM 모델 조사 보고서
한국석유관리원 내부 업무 및 폐쇄망 환경에서 활용 가능한 Small Language Model(SLM)의 기술적 특성과 활용 가능성을 분석한 보고서입니다.
---
o 분석 대상
항목	내용
모델	EXAONE-3.5-2.4B-Instruct
개발	LG AI Research
모델 유형	Instruction-tuned Bilingual SLM
파라미터	2.4B (실질 가중치 약 2.14B)
컨텍스트 길이	32,768 Tokens
아키텍처	Decoder-only Transformer
Attention	GQA (Grouped Query Attention)
토크나이저	BBPE 기반 · Vocab 102,400
양자화 지원	AWQ / GGUF
라이선스	EXAONE AI Model License 1.1-NC
---
o 주요 분석 내용
1. 모델 선택 배경
- 한국어 성능 우수
- 공공기관 폐쇄망 환경 적합
- 경량 온프레미스 배포 가능
- RAG 기반 문서 검색 활용성 확보
2.학습 및 튜닝 구조
- 6.5T 토큰 기반 사전학습
- 한국어·영어 50:50 비율
- SFT + DPO + SimPO 정렬
- Long-context 확장 학습 적용
3. 구조적 특징 분석
- 30-layer Decoder-only Transformer
- RoPE Scaling 적용
- GQA 기반 메모리 최적화
- 32K Context 지원
4. 모델 파일 구성
- `config.json`
- `model.safetensors`
- `tokenizer.json`
- `generation_config.json`
- `modeling_exaone.py`
5. 활용 가능 업무
- 법령 기반 RAG 질의응답
- 검사 규정 검색 시스템
- 내부 업무 AI Assistant
- 문서 요약 및 초안 생성
- 민원 응대 보조 시스템
6. 한계 및 주의사항
- 비상업(NC) 라이선스 제한
- 환각(Hallucination) 가능성
- 신뢰성 검증 필요
- 데이터셋 출처 비공개
- `trust_remote_code=True` 요구
---
o 활용 시나리오
- 한국석유관리원 내부 법령 질의응답 시스템
- EXAONE-3.5-2.4B-Instruct를 활용하여 다음과 같은 내부 업무용 RAG 시스템 구축 가능:
「석유사업법」 기반 질의응답,
시행령·시행규칙 자동 검색,
검사 매뉴얼 참조 시스템,
조문 근거 기반 답변 생성,
폐쇄망 환경 온프레미스 운영
---
o 기술적 강점
구분	특징
한국어 성능	동급 글로벌 모델 대비 우수
경량성	GGUF 기준 1.5~2GB 수준 운영 가능
장문 처리	32K Context 지원
RAG 적합성	법령·문서 검색 업무 최적화
배포 유연성	Ollama / llama.cpp / vLLM 지원
---
o 참고 링크
Hugging Face 모델 페이지  
https://huggingface.co/LGAI-EXAONE/EXAONE-3.5-2.4B-Instruct
EXAONE 공식 GitHub  
https://github.com/LG-AI-EXAONE/EXAONE-3.5
기술 보고서 (arXiv)  
https://arxiv.org/abs/2412.04862
EXAONE 모델 컬렉션  
https://huggingface.co/collections/LGAI-EXAONE/exaone-35-674d0e1bb3dcd2ab6f39dbb4
KoMT-Bench  
https://github.com/LG-AI-EXAONE/KoMT-Bench
Ollama 라이브러리  
https://ollama.com/library/exaone3.5:2.4b
---
작성자: 한국석유관리원_권용환 
