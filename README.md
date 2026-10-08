# MINI Dataset

한국어 대화 스타일과 인터넷 밈 관련 대화 데이터를 모은 JSON 저장소입니다.

## 파일과 형식

| 파일 | 형식 | 레코드 수 |
| --- | --- | ---: |
| [mini_style_dataset.json](mini_style_dataset.json) | `input` / `output` 배열 | 1,355 |
| [mini2.json](mini2.json) | `input` / `output` 배열 | 216 |
| [mini3.json](mini3.json) | `input` / `output` 배열 | 286 |
| [mini4.json](mini4.json) | `input` / `output` 배열 | 312 |
| [mini5.json](mini5.json) | `input` / `output` 배열 | 139 |
| [mini6.json](mini6.json) | `input` / `output` 배열 | 146 |
| [mini7 multi.json](mini7%20multi.json) | `messages` 배열 | 123 |
| [meme_dataset_2025.json](meme_dataset_2025.json) | `dataset_info` + `data` | 90 |

레코드 수는 각 파일을 JSON으로 파싱해 센 값입니다. 파일 간 중복을 제거한 고유 샘플 수는 아닙니다.

## 읽기

```python
import json
from pathlib import Path

pairs = json.loads(Path("mini_style_dataset.json").read_text(encoding="utf-8"))
print(pairs[0]["input"], pairs[0]["output"])

dialogues = json.loads(Path("mini7 multi.json").read_text(encoding="utf-8"))
print(dialogues[0]["messages"])
```

밈 데이터는 최상위 `data`를 읽습니다. 학습 파이프라인에 연결할 때 단일 턴 `input/output`과 여러 턴 `messages` 형식을 구분하세요.
