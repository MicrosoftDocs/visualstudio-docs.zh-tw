---
title: PROFILE_CURRENTID | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8e39234d9767be0cfb1305d25d107324ee073e7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792836"
---
# <a name="profilecurrentid"></a>PROFILE_CURRENTID
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 分析工具 API 參考 (原生)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [NameProfile](../profiling/nameprofile.md)   
 [ResumeProfile](../profiling/resumeprofile.md)   
 [StartProfile](../profiling/startprofile.md)   
 [StopProfile](../profiling/stopprofile.md)   
 [SuspendProfile](../profiling/suspendprofile.md)



