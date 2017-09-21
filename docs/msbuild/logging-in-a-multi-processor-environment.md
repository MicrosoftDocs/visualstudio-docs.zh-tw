---
title: "在多處理器環境中記錄 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 記錄"
  - "MSBuild, 多處理器記錄"
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# 在多處理器環境中記錄
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild雖能夠使用多個處理器來大幅縮短專案建置時間，但同時也增加了記錄的複雜性。  在單一處理器的環境中，記錄器能以可預期的循序方式處理傳入的事件、訊息、警告和錯誤。  但是，在多處理器環境中，來自於多個來源的事件可能會同時或不依順序到達。  MSBuild提供了能夠辨識多處理器的新記錄器，可讓您建立自訂「轉送記錄器」。  
  
## 記錄多處理器建置  
 當您在多處理器或多核心系統中建置一個或多個專案時，所有專案的MSBuild建置事件會同時產生。  記錄器可能會同時或不依順序收到大量的事件數據。  這可能會使記錄器不勝負荷，導致建置時間拉長、不正確記錄器輸出，甚至中斷建置。  為解決這些問題，MSBuild 記錄器可處理不依順序的事件，並將事件與其來源建立相互關聯。  
  
 您甚至可以建立自訂轉送記錄器，進一步提高記錄的效率。  自訂轉送記錄器的作用就如同篩選器，可讓您選擇在建置之前要監視的事件。  使用自訂轉送記錄器之後，就不會有不想要的事件造成記錄器不勝負荷、充斥記錄或拖慢建置速度。  
  
### 中央記錄模型  
 針對多處理器建置，MSBuild 會使用「中央記錄模型」。在中央記錄模型，MSBuild.exe 的一個執行個體會當做主要建置處理序 \(或稱為「中央節點」\)。MSBuild.exe 次要執行個體 \(或稱為「次要節點」\) 會附加到中央節點。  任何附加到中央節點的 ILogger 記錄器稱為「中央記錄器」，而附加到次要節點的記錄器稱為「次要記錄器」。  
  
 當建置進行時，次要記錄器會將其事件流量傳送到中央記錄器。  由於事件源自於數個次要節點，因此資料會同時但以交錯方式到達中央節點。  為解決事件對專案以及事件對目標參考的問題，事件引數還包含了額外的建置事件內容資訊。  
  
 雖然中央記錄器只需要實作 <xref:Microsoft.Build.Framework.ILogger>，但若要中央記錄器以參與建置的節點數目初始化，建議您一起實作 <xref:Microsoft.Build.Framework.INodeLogger>。  當引擎初始化記錄器時，會叫用 \(Invoke\) 下列 <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> 方法多載：  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### 分散式記錄模型  
 在中央記錄模型，如果有太多傳入訊息流量，例如一次有許多專案進行建置，可能會使中央節點不勝負荷，而造成系統負擔並降低建置效能。  
  
 為解決這個問題，MSBuild 也提供「分散式記錄模型」來延伸中央記錄模型，可讓您建立轉送記錄器。  轉送記錄器會附加到次要節點，從該節點接收傳入的建置事件。  轉送記錄器的作用就如同一般記錄器，唯一不同的是，它可以篩選事件，只將所需的事件轉送到中央節點。  這可減少中央節點的訊息流量，因此可提高效能。  
  
 您可以藉由實作衍生自 <xref:Microsoft.Build.Framework.ILogger> 的 <xref:Microsoft.Build.Framework.IForwardingLogger> 介面，來建立轉送記錄器。  介面會定義如下：  
  
```  
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 若要轉送在轉送記錄器中的事件，請呼叫 <xref:Microsoft.Build.Framework.IEventRedirector> 介面的 <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> 方法。  請將適當的 <xref:Microsoft.Build.Framework.BuildEventArgs> 或衍生項目當做參數傳遞。  
  
 如需詳細資訊，請參閱[建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)。  
  
### 附加分散式記錄器  
 若要在命令列建置上附加分散式記錄器，請使用 `/distributedlogger` \(簡寫為 `/dl`\) 參數。  指定記錄器類型和類別名稱的格式與 `/logger` 參數相同，唯一的差別在於分散式記錄器由兩個記錄類別組成：轉送記錄器和中央記錄器。  以下是附加分散式記錄器的範例：  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 星號 \(\*\) 會將 `/dl` 參數中的兩個記錄器名稱分隔開來。  
  
## 請參閱  
 [組建記錄器](../msbuild/build-loggers.md)   
 [建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)