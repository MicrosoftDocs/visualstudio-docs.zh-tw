---
title: 呼叫端-被呼叫端檢視 - 檢測資料 | Microsoft Docs
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
- Caller/Callee view
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc820808db428ec1b4919c5d65ca9e12091a987e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250545"
---
# <a name="callercallee-view---instrumentation-data"></a>呼叫端/被呼叫端檢視 - 檢測資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[呼叫端/被呼叫端] 檢視會在呼叫樹狀圖中顯示所選取函式及其父函式和子函式的分析資訊。 [呼叫端/被呼叫端] 檢視包含三個方格。  
  
 **目前的函式**會顯示在中間方格中，顯示所選取函式的分析資訊。 這些值包括對函式的所有呼叫。  
  
 **呼叫目前函式的函式**會顯示在上方方格中，顯示所選取函式之呼叫端 (父) 函式的分析資訊。 值表示目前函式 (從此呼叫端函式的呼叫所產生) 的值數量。  
  
 **目前的函式所呼叫的函式**會顯示在下方方格中，顯示所選取函式之被呼叫端 (子) 函式執行個體的分析資訊。 值表示在子函式 (由目前函式呼叫時) 中花費的時間。  
  
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
|**時間專有探查額外負荷**|檢測對這個函式造成的時間額外負荷。 已經從所有專有時間減去探查額外負荷。|  
|**時間內含探查額外負荷**|檢測對這個函式及其子函式所造成的時間額外負荷。 已經從所有內含時間減去探查額外負荷。|  
|**Type**|函式的內容︰<br /><br /> **0** - 目前的函式<br /><br /> **1** - 呼叫目前函式的函式<br /><br /> **2** - 目前的函式所呼叫的函式<br /><br /> 只在[VSPerfReport](../profiling/vsperfreport.md) 命令列的報表中。|  
|**根函式名稱**|目前函式的名稱。 只存在於 [VSPerfReport](../profiling/vsperfreport.md) 命令列報表中。|  
  
## <a name="elapsed-inclusive-values"></a>功能內含耗用值  
 功能內含耗用值表示函式在呼叫堆疊上的時間。 該時間包含在子函式中所花費的時間以及呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業。  
  
|資料行|描述|  
|------------|-----------------|  
|**功能內含耗用 (Elapsed Inclusive) 時間**|-  若為目前的函式，這是在函式中花費的時間。 該值包含在子函式中及呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業。<br />-  若為呼叫端函式，這是目前函式 (從此呼叫端函式的呼叫所產生) 的功能內含耗用 (Elapsed Inclusive) 時間量。<br />- 若為被呼叫端函式，這是此函式之執行個體 (從目前函式的呼叫所產生) 所花費的時間。 該值包含在被呼叫端之子函式中及呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業。|  
|**功能內含耗用 (Elapsed Inclusive) 時間 %**|在分析執行的總功能內含耗用時間中，花費在此內容中此函式之功能內含耗用時間的百分比。|  
|**平均功能內含耗用 (Elapsed Inclusive) 時間**|在此內容中呼叫此函式的平均功能內含耗用 (Elapsed Inclusive) 時間。|  
|**最大功能內含耗用 (Elapsed Inclusive) 時間**|在此內容中呼叫此函式的最大功能內含耗用 (Elapsed Inclusive) 時間。|  
|**最小功能內含耗用 (Elapsed Inclusive) 時間**|在此內容中呼叫此函式的最小功能內含耗用 (Elapsed Inclusive) 時間。|  
  
## <a name="elapsed-exclusive-values"></a>功能專屬耗用值  
 功能專屬耗用值表示函式直接在呼叫堆疊最上方執行的時間。 該時間包含呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業，但不包含在子函式中花費的時間。  
  
|資料行|描述|  
|------------|-----------------|  
|**功能專屬耗用 (Elapsed Exclusive) 時間**|-  若為目前的函式，這是直接執行函式所花費的時間。 該值包含在子函式中及呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業。<br />-  若為呼叫端函式，這是目前函式 (從此呼叫端函式的呼叫所產生) 的功能專屬耗用 (Elapsed Exclusive) 時間量。<br />- 若為被呼叫端函式，這是此函式之執行個體 (從目前函式的呼叫所產生) 所花費的時間。 該值排除在被呼叫端之子函式中所花費的時間，但是包含呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業。|  
|**功能專屬耗用 (Elapsed Exclusive) 時間 %**|在分析執行的總功能專屬耗用時間中，花費在此內容中此函式之總功能專屬耗用時間的百分比。|  
|**平均功能專屬耗用 (Elapsed Exclusive) 時間**|在此內容中呼叫此函式的平均功能專屬耗用 (Elapsed Exclusive) 時間。|  
|**最大功能專屬耗用 (Elapsed Exclusive) 時間**|在此內容中呼叫此函式的最大功能專屬耗用 (Elapsed Exclusive) 時間。|  
|**最小功能專屬耗用 (Elapsed Exclusive) 時間**|在此內容中呼叫此函式的最小功能專屬耗用 (Elapsed Exclusive) 時間。|  
  
## <a name="application-inclusive-values"></a>應用程式內含值  
 應用程式內含值表示函數在呼叫堆疊上的時間。 該時間不包含呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業，但包含在子函式中花費的時間。  
  
|資料行|描述|  
|------------|-----------------|  
|**應用程式內含 (Application Inclusive) 時間**|-  若為目前的函式，這是在函式及其子函式中花費的時間。 該值排除呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業。<br />-  若為呼叫端函式，這是目前函式 (從此呼叫端函式的呼叫所產生) 的應用程式內含時間量。<br />- 若為被呼叫端函式，這是此函式之執行個體 (從目前函式的呼叫所產生) 所花費的時間。 該值包含在被呼叫端函式之子函式中所花費的時間，但不包含呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業。|  
|**應用程式內含 (Application Inclusive) 時間 %**|在分析執行的總功能內含耗用時間中，花費在此內容中此函式之總應用程式內含時間的百分比。|  
|**平均應用程式內含 (Application Inclusive) 時間**|在此內容中呼叫此函式的平均應用程式內含 (Application Inclusive) 時間。|  
|**最大應用程式內含 (Application Inclusive) 時間**|在此內容中呼叫此函式的最大應用程式內含 (Application Inclusive) 時間。|  
|**最小應用程式內含 (Application Inclusive) 時間**|在此內容中呼叫此函式的最小應用程式內含 (Application Inclusive) 時間。|  
  
## <a name="application-exclusive-values"></a>應用程式專屬值  
 應用程式專屬值表示在函式中花費的時間。 這排除在子函式中花費的時間，同時也排除呼叫作業系統的時間，例如內容切換和輸入/輸出作業。  
  
|Column|描述|  
|------------|-----------------|  
|**應用程式專屬 (Application Exclusive) 時間**|-  若為目前的函式，這是直接執行函式所花費的時間。 這不包含在子函式中花費的時間，也不包含呼叫作業系統的時間，例如內容切換和輸入/輸出作業。<br />-  若為呼叫端函式，這是目前函式 (從此呼叫端函式的呼叫所產生) 的應用程式專屬時間量。<br />- 若為被呼叫端函式，這是此函式之執行個體 (從目前函式的呼叫所產生) 所花費的時間。 這不包含在被呼叫端函式之子函式中花費的時間，也不包含呼叫作業系統的時間，例如內容切換和輸入/輸出作業。|  
|**應用程式專屬 (Application Exclusive) 時間 %**|在分析執行的總功能專屬耗用時間中，花費在此內容中此函式之總應用程式專屬時間的百分比。|  
|**平均應用程式專屬 (Application Exclusive) 時間**|在此內容中呼叫此函式的平均應用程式專屬 (Application Exclusive) 時間。|  
|**最大應用程式專屬 (Application Exclusive) 時間**|在此內容中呼叫此函式的最大應用程式專屬 (Application Exclusive) 時間。|  
|**最小應用程式專屬 (Application Exclusive) 時間**|在此內容中呼叫此函式的最小應用程式專屬 (Application Exclusive) 時間。|  
  
## <a name="see-also"></a>另請參閱  
 [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)   
 [呼叫端/被呼叫端檢視 - 取樣資料](../profiling/caller-callee-view-sampling-data.md)   
 [呼叫端/被呼叫端檢視 - .NET 記憶體取樣資料](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [呼叫端/被呼叫端檢視 - .NET 記憶體檢測資料](../profiling/caller-callee-view-net-memory-instrumentation-data.md)



