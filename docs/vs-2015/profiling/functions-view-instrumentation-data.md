---
title: 函式檢視 - 檢測資料 | Microsoft Docs
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
- Function view
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c19175af6af583120c9fd648328ecf90deaeb3a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786796"
---
# <a name="functions-view---instrumentation-data"></a>函式檢視 - 檢測資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

函式報表檢視會依函式名稱列出程式碼剖析資料。  
  
## <a name="general"></a>一般  
 一般資料行會識別檢視列中的函式。  
  
|資料行|描述|  
|------------|-----------------|  
|**函式名稱**|函式的名稱。|  
|**函式位址**|函式的位址。|  
|**函式行號**|原始程式檔中這個函式的開頭行號。|  
|**呼叫次數**|呼叫此函式的總次數。|  
|**原始程式檔**|含有這個函式定義的原始程式檔。|  
|**模組名稱**|包含該函式的模組名稱。|  
|**模組路徑**|包含該函式的模組路徑。|  
|**處理序 ID**|分析執行的處理序 ID (PID)。|  
|**處理序名稱**|處理序的名稱。|  
|**時間專有探查額外負荷**|檢測對這個函式造成的時間額外負荷。 其中不包括此函式所呼叫函式中的額外負荷。 已經從所有專有時間減去探查額外負荷。|  
|**時間內含探查額外負荷**|檢測對這個函式及其子函式所造成的時間額外負荷。 其中包括此函式所呼叫函式中的額外負荷。 已經從所有內含時間減去探查額外負荷。|  
  
## <a name="elapsed-inclusive-values"></a>功能內含耗用值  
 功能內含耗用值表示函式在呼叫堆疊上的時間。 該時間包含函式呼叫函式以及呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業。  
  
|資料行|描述|  
|------------|-----------------|  
|**功能內含耗用 (Elapsed Inclusive) 時間**|這個函式的所有呼叫的功能內含耗用 (Elapsed Inclusive) 時間總計。|  
|**功能內含耗用 (Elapsed Inclusive) 時間 %**|在此函式的功能內含耗用時間內，花費在程式碼剖析執行的總功能內含耗用時間百分比。|  
|**平均功能內含耗用 (Elapsed Inclusive) 時間**|呼叫這個函式的平功能內含耗用 (Elapsed Inclusive) 時間。|  
|**最大功能內含耗用 (Elapsed Inclusive) 時間**|呼叫這個函式的最大功能內含耗用 (Elapsed Inclusive) 時間。|  
|**最小功能內含耗用 (Elapsed Inclusive) 時間**|呼叫這個函式的最小功能內含耗用 (Elapsed Inclusive) 時間。|  
  
## <a name="elapsed-exclusive-values"></a>功能專屬耗用值  
 功能專屬耗用值表示函式在函式主體中執行程式碼所花的時間，亦即函式在呼叫堆疊最上方的時間。 該時間包含呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業，但不包含在函式所呼叫函式中花的時間。  
  
|資料行|描述|  
|------------|-----------------|  
|**功能專屬耗用 (Elapsed Exclusive) 時間**|這個函式的所有呼叫的功能專屬耗用 (Elapsed Exclusive) 時間總計。|  
|**功能專屬耗用 (Elapsed Exclusive) 時間 %**|在此函式的總功能專屬耗用時間內，花費在分析執行的總功能專屬耗用時間百分比。|  
|**平均功能專屬耗用 (Elapsed Exclusive) 時間**|呼叫這個函式的平均功能專屬耗用 (Elapsed Exclusive) 時間。|  
|**最大功能專屬耗用 (Elapsed Exclusive) 時間**|呼叫這個函式的最大功能專屬耗用 (Elapsed Exclusive) 時間。|  
|**最小功能專屬耗用 (Elapsed Exclusive) 時間**|呼叫這個函式的最小功能專屬耗用 (Elapsed Exclusive) 時間。|  
  
## <a name="application-inclusive-values"></a>應用程式內含值  
 應用程式內含值表示函數在呼叫堆疊上的時間。 該時間不包含呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業，但包含在函式所呼叫函式中花的時間。  
  
|資料行|描述|  
|------------|-----------------|  
|**應用程式內含 (Application Inclusive) 時間**|這個函式所有呼叫的總應用程式內含 (Application Inclusive) 時間。|  
|**應用程式內含 (Application Inclusive) 時間 %**|此函式的總應用程式內含時間內，花費在分析執行的總功能內含耗用時間百分比。|  
|**平均應用程式內含 (Application Inclusive) 時間**|呼叫此函數的平均應用程式內含 (Application Inclusive) 時間。|  
|**最大應用程式內含 (Application Inclusive) 時間**|呼叫此函式的最大應用程式內含 (Application Inclusive) 時間。|  
|**最小應用程式內含 (Application Inclusive) 時間**|呼叫此函式的最小應用程式內含 (Application Inclusive) 時間。|  
  
## <a name="application-exclusive-values"></a>應用程式專屬值  
 應用程式專屬值表示函數直接在呼叫堆疊最上方執行的時間。 該時間不包含呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業，且不包含在函式所呼叫函式中花的時間。  
  
|資料行|描述|  
|------------|-----------------|  
|**應用程式專屬 (Application Exclusive) 時間**|這個函式所有呼叫的總應用程式專屬 (Application Inclusive) 時間。|  
|**應用程式專屬 (Application Exclusive) 時間 %**|此函式的總應用程式專屬時間內，花費在分析執行的總功能專屬耗用時間百分比。|  
|**平均應用程式專屬 (Application Exclusive) 時間**|呼叫此函式的平均應用程式專屬 (Application Exclusive) 時間。|  
|**最大應用程式專屬 (Application Exclusive) 時間**|呼叫此函式的最大應用程式專屬 (Application Exclusive) 時間。|  
|**最小應用程式專屬 (Application Exclusive) 時間**|呼叫此函式的最小應用程式專屬 (Application Exclusive) 時間。|  
  
## <a name="see-also"></a>另請參閱  
 [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)   
 [函式檢視](../profiling/functions-view-sampling-data.md)   
 [函式檢視 - 取樣](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [函式檢視 - 檢測](../profiling/functions-view-dotnet-memory-instrumentation-data.md)



