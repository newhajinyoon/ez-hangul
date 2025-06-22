# ez-hangul

한글 자모 분리/조합, 조사 처리, 순우리말 변환을 위한 Python 라이브러리

# [깃허브](https://github.com/newhajinyoon/ez-hangul)

## 기능

```
pip install ez-hangul
```

```python
from ez_hangul import *
```

### 🔤 자모 분리/조합

한글 문자를 자모 단위로 분리하고 다시 조합할 수 있습니다.

```python
import hangul_jamo as hj

# 기본 자모 분리
split_text = split("안녕하세요")
print(split_text)  # ㅇㅏㄴㄴㅕㅇㅎㅏㅅㅔㅇㅛ

# 기본 자모 결합
added_text = add("ㅇㅏㄴㄴㅕㅇㅎㅏㅅㅔㅇㅛ")
print(added_text)  # 안녕하세요
```

### 🔀 쌍자음/겹자음 처리

쌍자음과 겹자음을 낱자로 완전히 분해하거나 다시 결합할 수 있습니다.

```python
# 쌍자음/겹자음까지 분해
heavy_split_text = heavy_split("안녕하쎄요")
print(heavy_split_text)  # ㅇㅏㄴㄴㅕㅇㅎㅏㅅㅅㅔㅇㅛ

# 쌍자음/겹자음 결합
heavy_added_text = heavy_add("ㅇㅏㄴㄴㅕㅇㅎㅏㅅㅅㅔㅇㅛ")
print(heavy_added_text)  # 안녕하쎄요
```

### 🎯 초성 추출

문자열에서 각 글자의 초성만 추출합니다.

```python
print(getChoseong("안녕하세요"))  # ㅇㄴㅎㅅㅇ
```

### 📝 조사 자동 처리

한국어 조사를 문법에 맞게 자동으로 붙여줍니다.

```python
print(josa('사과', '을/를'))  # 사과를
print(josa('사과', '과/와'))  # 사과와
print(josa('물', '을/를'))    # 물을
print(josa('물', '과/와'))    # 물과
```

### 🔧 조사 자동 수정

겹쳐 표기된 조사를 문맥에 맞게 자동으로 수정합니다.

```python
print(compjosa("사과을(를) 먹었는데 지렁이이/가 나타났다!"))
# 출력: 사과를 먹었는데 지렁이가 나타났다!
```

### 🔄 완성형/조합형 변환

완성형 한글과 조합형 한글 간 변환을 지원합니다.

```python
# 완성형 → 조합형
print(toCompat("안녕"))

# 조합형 → 완성형  
print(fromCompat("안녕"))
```

### 🌸 순우리말 변환

숫자를 순우리말로 변환할 수 있습니다.

```python
# 날짜를 순우리말로
print(native_day(1))   # 하루
print(native_day(4))   # 나흘
print(native_day(6))   # 엿새
print(native_day(31))  # 31일

# 숫자를 순우리말로
print(native_number(1))   # 하나
print(native_number(28))  # 스물여덟
print(native_number(99))  # 아흔아홉
```

## 전체 예제

```python
from ez_hangul import *

if __name__ == "__main__":
    # 자모 분리/조합
    split_text = split("안녕하세요")
    print(f"분리: {split_text}")
    
    added_text = add(split_text)
    print(f"조합: {added_text}")
    
    # 초성 추출
    print(f"초성: {getChoseong('안녕하세요')}")
    
    # 조사 처리
    print(josa('사과', '을/를'))
    print(josa('책', '이/가'))
    
    # 순우리말 변환
    print(f"3일: {native_day(3)}")
    print(f"15: {native_number(15)}")
```

## API 레퍼런스

### 자모 처리
- `split(text)`: 한글을 자모로 분리
- `add(jamo_text)`: 자모를 한글로 조합
- `heavy_split(text)`: 쌍자음까지 완전 분리
- `heavy_add(jamo_text)`: 쌍자음 포함 조합
- `getChoseong(text)`: 초성 추출

### 조사 처리
- `josa(word, josa_type)`: 조사 자동 붙이기
- `compjosa(text)`: 잘못된 조사 자동 수정

### 인코딩 변환
- `toCompat(text)`: 완성형 → 조합형
- `fromCompat(text)`: 조합형 → 완성형

### 순우리말 변환
- `native_day(number)`: 날짜를 순우리말로
- `native_number(number)`: 숫자를 순우리말로

## 기여하기

버그 리포트나 기능 제안은 GitHub Issues를 통해 해주세요.
