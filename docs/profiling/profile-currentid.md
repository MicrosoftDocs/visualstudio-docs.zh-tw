---
title: PROFILE_CURRENTID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e0f0275e7123db9febaeaf05f231053818665df
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="profilecurrentid"></a>PROFILE_CURRENTID
PROFILE_CURRENTID 在對 NameProfile、StartProfile、StopProfile、SuspendProfile 和 ResumeProfile 函式的呼叫中，會傳回執行緒識別碼或處理序識別碼的虛擬權杖。 使用它會讓函式在目前的執行緒或處理序上作業，而不是特別指定的執行緒或處理序。  
  
## <a name="example"></a>範例  
 PROFILE_CURRENTID 在 VSPerf.h 中定義為：  
  
```  
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;  
```  
  
## <a name="example"></a>範例  
 以下範例會示範 PROFILE_CURRENTID。 此範例使用 PROFILE_CURRENTID 為參數，在對 [StartProfile](../profiling/startprofile.md) 函式的呼叫中識別目前的執行緒。  
  
```  
void ExerciseProfileCurrentID()  
{  
    // Declare ProfileOperationResult enumeration   
    // to hold return value of a call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    profileResult = StartProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StartProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 分析工具 API 參考 (原生)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [NameProfile](../profiling/nameprofile.md)   
 [ResumeProfile](../profiling/resumeprofile.md)   
 [StartProfile](../profiling/startprofile.md)   
 [StopProfile](../profiling/stopprofile.md)   
 [SuspendProfile](../profiling/suspendprofile.md)