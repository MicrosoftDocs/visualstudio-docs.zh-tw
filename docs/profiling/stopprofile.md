---
title: StopProfile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- StopProfile
ms.assetid: be75b03c-7af5-4abe-a54a-6ee5479ad877
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b44726b2ce1f7a0b699898edfc3a53371163168e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952231"
---
# <a name="stopprofile"></a>StopProfile
`StopProfile` 函式會將所指定分析層級的計數器設定為 0 (關閉)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
PROFILE_COMMAND_STATUS PROFILERAPI StopProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### <a name="parameters"></a>參數  
 `Level`  
  
 指出可套用效能資料收集的分析層級。 下列 **PROFILE_CONTROL_LEVEL** 列舉程式可以用來指出可套用效能資料收集的三種層級的其中一種：  
  
|列舉值|說明|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|全域層級設定會影響分析執行中的所有處理序和執行緒。|  
|PROFILE_PROCESSLEVEL|處理序層級設定會影響屬於所指定處理序的所有執行緒。|  
|PROFILE_THREADLEVEL|執行緒分析層級設定會影響指定的執行緒。|  
  
 `dwId`  
  
 系統產生的處理序或執行緒識別碼。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 此函式會使用 **PROFILE_COMMAND_STATUS** 列舉來指出成功或失敗。 傳回值可以是下列其中一個：  
  
|列舉值|說明|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|分析項目識別碼不存在。|  
|PROFILE_ERROR_LEVEL_NOEXIST|指定的分析層級不存在。|  
|PROFILE_ERROR_MODE_NEVER|呼叫函式時，分析模式設定為 NEVER。|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|尚未實作分析函式呼叫、分析層級或呼叫與層級的組合。|  
|PROFILE_OK|呼叫成功。|  
  
## <a name="remarks"></a>備註  
 StartProfile 和 StopProfile 可控制分析層級的開始/停止狀態。 開始/停止的預設值為 1。 您可以變更登錄中的起始值。 每個 StartProfile 呼叫都會將開始/停止設定為 1；每個 StopProfile 呼叫都會將它設定為 0。  
  
 開始/停止大於 0 時，層級的開始/停止狀態會是 ON。 當它小於或等於 0 時，開始/停止狀態為 OFF。  
  
 當開始/停止狀態以及暫止/繼續狀態都是 ON 時，層級的分析狀態就會是 ON。 針對要分析的執行緒，其全域、處理序和執行緒層級狀態都必須是 ON。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>函式資訊  
 標頭：在 VSPerf.h 中宣告  
  
 匯入程式庫：VSPerf.lib  
  
## <a name="example"></a>範例  
 下列範例說明 StopProfile 方法。 此範例假設已對 [PROFILE_CURRENTID](../profiling/profile-currentid.md) 識別出的相同執行緒或處理序呼叫 StartProfile 方法。  
  
```cpp  
void ExerciseStopProfile()  
{  
    // StartProfile and StopProfile control the   
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to StopProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StopProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StopProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 分析工具 API 參考 (原生)](../profiling/visual-studio-profiler-api-reference-native.md)