---
title: FormatFromRawValue 함수 (관리 되지 않는 API 참조)
description: FormatFromRawValue 함수는 원시 성능 데이터를 지정 된 형식으로 변환 합니다.
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e678aca5baf82c07ec9fc5c85cef22630af5ab0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672333"
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue 함수

형식 변환이 시간 기반인 경우 하나의 원시 성능 데이터 값을 지정된 형식으로 변화하거나 두 개의 원시 성능 데이터 값으로 변환합니다.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>구문

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType,
   [in] uint                    dwFormat,
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
);
```

## <a name="parameters"></a>매개 변수

`dwCounterType`\
진행 카운터 형식입니다. 카운터 형식 목록은 [WMI 성능 카운터 형식](/windows/desktop/WmiSdk/wmi-performance-counter-types)을 참조 하세요. `dwCounterType` 는 및를 제외한 모든 카운터 형식일 수 있습니다 `PERF_LARGE_RAW_FRACTION` `PERF_LARGE_RAW_BASE` .

`dwFormat`\
진행 원시 성능 데이터를 변환할 대상 형식입니다. 다음 값 중 하나일 수 있습니다.

|상수  |값  |설명 |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | 계산 된 값을 배정밀도 부동 소수점 값으로 반환 합니다. |
| `PDH_FMT_LARGE` | 0x00000400 | 계산 된 값을 64 비트 정수로 반환 합니다. |
| `PDH_FMT_LONG` | 0x00000100 | 계산 된 값을 32 비트 정수로 반환 합니다. |

이전 값 중 하나는 다음 크기 조정 플래그 중 하나를 사용 하 여 ORed 수 있습니다.

|상수  |값  |설명 |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | 카운터의 배율 인수를 적용 하지 마십시오. |
| `PDH_FMT_1000` | 0x00002000 | 최종 값을 1000에 곱합니다. |

`pTimeBase`\
진행 형식 변환에 필요한 경우 시간 기준에 대 한 포인터입니다. 형식 변환에 시간 기준 정보가 필요 하지 않은 경우이 매개 변수 값은 무시 됩니다.

`pRawValue1`\
진행 [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) 원시 성능 값을 나타내는 구조체에 대 한 포인터입니다.

`pRawValue2`\
진행 [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) 두 번째 원시 성능 값을 나타내는 구조체에 대 한 포인터입니다. 두 번째 원시 성능 값이 필요 하지 않은 경우이 매개 변수는 이어야 `null` 합니다.

`pFmtValue`\
제한이 [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) 형식이 지정 된 성능 값을 받는 구조체에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

이 함수에서 반환 되는 값은 다음과 같습니다.

|상수  |값  |설명  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | 함수 호출이 성공 했습니다. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | 필요한 인수가 없거나 잘못 되었습니다. |
| `PDH_INVALID_HANDLE` | 0xC0000BBC | 핸들이 올바른 PDH 개체가 아닙니다. |

## <a name="remarks"></a>설명

이 함수는 [FormatFromRawValue](/previous-versions/ms231047(v=vs.85)) 함수에 대 한 호출을 래핑합니다.

## <a name="requirements"></a>요구 사항

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.

 **라이브러리:** PerfCounter.dll

 **.NET Framework 버전:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>참조

- [WMI 및 성능 카운터(관리되지 않는 API 참조)](index.md)
