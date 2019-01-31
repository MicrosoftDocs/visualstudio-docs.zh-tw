---
title: 在多處理器環境中記錄 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1afca269788710b3bf7a3ebf6fceea2f10b49a27
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788108"
---
# <a name="logging-in-a-multi-processor-environment"></a>在多處理器環境中記錄
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
MSBuild 雖能夠使用多個處理器來大幅縮短專案建置時間，但同時也增加了記錄的複雜性。 在單一處理器環境中，記錄器可以透過可預測的循序方式來處理傳入的事件、訊息、警告和錯誤。 不過，在多處理器環境中，來自數個來源的事件可能會同時或不依順序到達。 MSBuild 提供可辨識多處理器的新記錄器，並啟用建立自訂「轉送記錄器」。  
  
## <a name="logging-multiple-processor-builds"></a>記錄多處理器建置  
 當您在多處理器或多核心系統中建置一個或多個專案時，所有專案的 MSBuild 建置事件會同時產生。 記錄器可能會同時或不依順序收到大量的事件資料。 這可能會讓記錄器不勝負荷，導致建置時間拉長、不正確記錄器輸出，甚至中斷建置。 為解決這些問題，MSBuild 記錄器可處理不依順序的事件，並將事件與其來源建立相互關聯。  
  
 建立自訂轉送記錄器，甚至可以改善更多的記錄效率。 自訂轉送記錄器可讓您在建置之前選擇您要監視的事件，以作為篩選。 當您使用自訂轉送記錄器時，不想要的事件不會讓記錄器不勝負荷、導致記錄雜亂，或讓建置時間變慢。  
  
### <a name="central-logging-model"></a>中央記錄模型  
 針對多處理器建置，MSBuild 會使用「中央記錄模型」。 在中央記錄模型中，MSBuild.exe 執行個體作為主要建置處理序或「中央節點」。 次要 MSBuild.exe 執行個體或「次要節點」會附加至中央節點。 任何附加至中央節點的 ILogger 記錄器都會稱為「中央記錄器」，而附加至次要節點的記錄器稱為「次要記錄器」。  
  
 進行建置時，次要記錄器會將其事件流量路由傳送至中央記錄器。 因為事件產生自數個次要節點，所以資料會同時但交錯地到達中央節點。 為了解析事件對專案和事件對目標參考，事件引數會包含其他建置事件內容資訊。  
  
 雖然中央記錄器只需要實作 <xref:Microsoft.Build.Framework.ILogger>，但是如果您想要中央記錄器使用參與建置的節點數目初始化，也建議一併實作 <xref:Microsoft.Build.Framework.INodeLogger>。 引擎初始化記錄器時，會叫用 <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> 方法的下列多載：  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### <a name="distributed-logging-model"></a>分散式記錄模型  
 在中央記錄模型中，太多傳入的訊息流量 (例如，一次有許多專案建置時) 可能會讓中央節點不勝負荷，而造成系統壓力並降低建置效能。  
  
 為了減少此問題，MSBuild 也可讓您建立轉送記錄器，以啟用可擴充中央記錄模型的「分散式記錄模型」。 轉送記錄器會附加至次要節點，並從該節點中接收傳入的建置事件。 轉送記錄器就像一般記錄器，差異在於它可以篩選事件，然後只將所需的事件轉送至中央節點。 這會減少中央節點的訊息流量，因此可啟用較佳的效能。  
  
 您可以實作衍生自 <xref:Microsoft.Build.Framework.ILogger> 的 <xref:Microsoft.Build.Framework.IForwardingLogger> 介面來建立轉送記錄器。 介面定義如下：  
  
```  
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 若要在轉送記錄器中轉送事件，請呼叫 <xref:Microsoft.Build.Framework.IEventRedirector> 介面的 <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> 方法。 傳遞適當的 <xref:Microsoft.Build.Framework.BuildEventArgs> 或系出物件作為參數。  
  
 如需詳細資訊，請參閱[建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)。  
  
### <a name="attaching-a-distributed-logger"></a>附加分散式記錄器  
 若要在命令列建置上附加分散式記錄器，請使用 `/distributedlogger` (或者，簡稱是 `/dl`) 參數。 用於指定記錄器類型和類別名稱的格式與 `/logger` 參數相同，差異在於分散式記錄器包含兩個記錄類別：轉送記錄器和中央記錄器。 以下是附加分散式記錄器範例：  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 星號 (*) 可分隔 `/dl` 參數中的兩個記錄器名稱。  
  
## <a name="see-also"></a>請參閱  
 [組建記錄器](../msbuild/build-loggers.md)   
 [建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)
