---
title: "撰寫能夠辨識多處理器的記錄器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "記錄器, 多處理器"
  - "msbuild, 辨識多處理器的記錄器"
  - "多處理器的記錄器"
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 撰寫能夠辨識多處理器的記錄器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 雖能夠使用多個處理器來大幅縮短專案建置時間，但同時也增加了建置事件記錄的複雜性。  在單一處理器的環境中，事件、訊息、警告和錯誤會以可預期而且循序的方式到達記錄器。  但是，在多處理器環境中，來自於不同來源的事件可能會同時或不依順序到達。  為解決這個問題，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 提供了能夠辨識多處理器的記錄器以及新的記錄模型，可讓您建立自訂的「轉送記錄器」。  
  
## 多處理器記錄的挑戰  
 當您在多處理器或多核心系統中建置一個或多個專案時，所有專案的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 建置事件會同時產生。  記錄器可能會同時或不依順序收到大量的事件訊息。  由於 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 記錄器沒有處理這種情況的設計，這可能會使記錄器不勝負荷，導致建置時間拉長、記錄器輸出不正確，甚至中斷建置。  為解決這些問題，記錄器 \(從 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 開始\) 可處理不依順序的事件，並將事件與其來源建立相互關聯。  
  
 您甚至可以建立自訂轉送記錄器，進一步提高記錄的效率。  自訂轉送記錄器的作用就如同篩選器，可讓您選擇在建置之前只要監視的事件。  使用自訂轉送記錄器之後，就不會有不想要的事件造成記錄器不勝負荷、充斥記錄或拖慢建置速度。  
  
## 多處理器記錄模型  
 為解決與多處理器相關的建置問題，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 支援兩種記錄模式，分別為中央和分散式。  
  
### 中央記錄模型  
 在中央記錄模型，MSBuild.exe 的單一執行個體會當做「中央節點」，而中央節點的子執行個體 \(稱為「次要節點」\) 會附加到中央節點，協助其執行建置工作。  
  
 ![中央記錄器模型](~/msbuild/media/centralnode.png "CentralNode")  
  
 附加到中央節點的各種類型記錄器稱為「中央記錄器」。每種記錄器類型同時間只能有一個執行個體附加到中央節點。  
  
 當建置進行時，次要節點會將其建置事件傳送到中央節點。  中央節點會將本身的所有事件以及次要節點的事件傳送到一個或多個附加的中央記錄器。  記錄器接著會根據傳入的資料建立記錄檔。  
  
 雖然中央記錄器只需要實作 <xref:Microsoft.Build.Framework.ILogger>，但建議您一起實作 <xref:Microsoft.Build.Framework.INodeLogger>，讓記錄器能夠以參與建置的節點數目初始化。  當引擎初始化記錄器時，會叫用 \(Invoke\) 下列 <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> 方法多載。  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
 任何已存在的 <xref:Microsoft.Build.Framework.ILogger> 記錄器都可以當做中央記錄器，並可附加到建置。  不過，中央記錄器若在撰寫時沒有明確加入多處理器記錄案例和不依順序事件的支援，可能會中斷建置或產生無意義的輸出。  
  
### 分散式記錄模型  
 在中央記錄模型，傳入的訊息流量若太多，可能會使中央節點不勝負荷，例如，同時間有許多專案進行建置。  這可能會造成系統資源負擔並降低建置效能。  為解決這個問題，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 支援分散式記錄模型。  
  
 ![分散式記錄模型](~/msbuild/media/distnode.png "DistNode")  
  
 分散式記錄模型是中央記錄模型的延伸，可讓您建立轉送記錄器。  
  
#### 轉送記錄器  
 轉送記錄器是輕量型的次要記錄器，其事件篩選器會附加到次要節點，從該節點接收傳入的建置事件。  它會篩選傳入的事件，只將您所指定的事件轉送到中央節點。  這可減少傳送到中央節點的訊息流量，進而提高整體建置效能。  
  
 分散式記錄的使用方式有下列兩種：  
  
-   自訂名為 <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> 的預先建立轉送記錄器。  
  
-   自行撰寫自訂轉送記錄器。  
  
 您可以修改 ConfigurableForwardingLogger 來符合需求。  若要執行這項作業，請在命令列上使用 MSBuild.exe 呼叫記錄器，然後列出要記錄器轉送到中央節點的建置事件。  
  
 或者，您也可以建立自訂轉送記錄器。  藉由建立自訂轉送記錄器，您可以調整記錄器的行為。  不過，建立自訂轉送記錄器要比單純自訂 ConfigurableForwardingLogger 複雜。  如需詳細資訊，請參閱[建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)。  
  
## 使用 ConfigurableForwardingLogger 進行簡單分散式記錄  
 若要附加 ConfigurableForwardingLogger 或自訂轉送記錄器，請在 MSBuild.exe 命令列建置中使用 `/distributedlogger` 參數 \(簡寫為 `/dl`\)。  指定記錄器類型和類別名稱的格式與 `/logger` 參數，唯一的差別在於分散式記錄器一定會有轉送記錄器和中央記錄器這兩個記錄類別，而不只有一個。  下列範例說明如何附加名為 XMLForwardingLogger 的自訂轉送記錄器。  
  
```  
msbuild.exe myproj.proj/distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral  
```  
  
> [!NOTE]
>  星號 \(\*\) 必須用來將 `/dl` 參數中的兩個記錄器名稱分隔開來。  
  
 使用 ConfigurableForwardingLogger 就像使用任何其他記錄器 \(如 [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)所述\) 一樣，唯一的差別在於附加的是 ConfigurableForwardingLogger 記錄器而非一般 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 記錄器，而指定的參數是要 ConfigurableForwardingLogger 傳送到中央節點的事件。  
  
 例如，如果只要在建置開始和結束以及發生錯誤時收到通知，請將 `BUILDSTARTEDEVENT`、`BUILDFINISHEDEVENT` 和 `ERROREVENT` 當做參數傳遞。  您可以傳遞多個參數，只要使用分號隔開參數即可。  下列範例說明如何使用 ConfigurableForwardingLogger 只轉送 `BUILDSTARTEDEVENT`、`BUILDFINISHEDEVENT` 和 `ERROREVENT` 事件。  
  
```  
msbuild.exe myproj.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT  
```  
  
 以下是可用 ConfigurableForwardingLogger 參數的清單。  
  
|ConfigurableForwardingLogger 參數|  
|-------------------------------------|  
|BUILDSTARTEDEVENT|  
|BUILDFINISHEDEVENT|  
|PROJECTSTARTEDEVENT|  
|PROJECTFINISHEDEVENT|  
|TARGETSTARTEDEVENT|  
|TARGETFINISHEDEVENT|  
|TASKSTARTEDEVENT|  
|TASKFINISHEDEVENT|  
|ERROREVENT|  
|WARNINGEVENT|  
|HIGHMESSAGEEVENT|  
|NORMALMESSAGEEVENT|  
|LOWMESSAGEEVENT|  
|CUSTOMEVENT|  
|COMMANDLINE|  
|PERFORMANCESUMMARY|  
|NOSUMMARY|  
|SHOWCOMMANDLINE|  
  
## 請參閱  
 [建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)