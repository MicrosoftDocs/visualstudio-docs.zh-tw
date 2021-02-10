---
title: ResumeProfile | Microsoft Docs
description: 瞭解 ResumeProfile 方法如何遞減指定分析層級的暫止/繼續計數器。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ResumeProfile
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5607efbf9e979ff427d772089731af01cdd71867
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950152"
---
# <a name="resumeprofile"></a>ResumeProfile
`ResumeProfile` 方法會遞減指定分析層級的暫止/繼續計數器。

## <a name="syntax"></a>語法

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>參數
 `Level`

 指出可套用效能資料收集的分析層級。 下列 **PROFILE_CONTROL_LEVEL** 列舉程式可以用來指出可套用效能資料收集的三種層級的其中一種：

|列舉值|Description|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|全域層級設定會影響分析執行中的所有處理序和執行緒。|
|PROFILE_PROCESSLEVEL|處理序層級設定會影響屬於所指定處理序的所有執行緒。|
|PROFILE_THREADLEVEL|執行緒分析層級設定會影響指定的執行緒。|

 `dwId`

 系統產生的處理序或執行緒識別碼。

## <a name="property-valuereturn-value"></a>屬性值/傳回值
 此函式會使用 **PROFILE_COMMAND_STATUS** 列舉來指出成功或失敗。 傳回值可以是下列其中一個：

|列舉值|Description|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|分析項目識別碼不存在。|
|PROFILE_ERROR_LEVEL_NOEXIST|指定的分析層級不存在。|
|PROFILE_ERROR_MODE_NEVER|呼叫函式時，分析模式設定為 NEVER。|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|尚未實作分析函式呼叫、分析層級或呼叫與層級的組合。|
|PROFILE_OK|呼叫成功。|

## <a name="remarks"></a>備註
 暫止/繼續計數器的初始值為 0。 每次呼叫 SuspendProfile，暫止/繼續計數即加 1；每次呼叫 ResumeProfile 則減 1。

 暫止/繼續計數大於 0 時，層級的暫止/繼續狀態為 OFF。 當計數小於或等於 0 時，暫止/繼續狀態為 ON。

 當開始/停止狀態以及暫止/繼續狀態都是 ON 時，層級的分析狀態就會是 ON。 至於要分析的執行緒，其全域、處理序和執行緒層級的狀態必須全部為 ON。

## <a name="net-framework-equivalent"></a>.NET Framework 同等
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>函式資訊
 標頭：在 *VSPerf.h* 中宣告

 匯入程式庫：*VSPerf.lib*

## <a name="example"></a>範例
 下面範例示範 ResumeProfile 函式。 這個範例假設已對 [PROFILE_CURRENTID](../profiling/profile-currentid.md) 識別出的相同執行緒或處理序呼叫 SuspendProfile 方法。

```cpp
void ExerciseResumeProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the Suspend/Resume
    // count; each call to ResumeProfile subtracts 1.

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call to ResumeProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = ResumeProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("ResumeProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>另請參閱
- [Visual Studio profiler API 參考 (原生) ](../profiling/visual-studio-profiler-api-reference-native.md)
