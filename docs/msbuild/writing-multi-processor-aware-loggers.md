---
title: 撰寫能夠辨識多處理器的記錄器 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9d73e1748be34dda6913937ce71858b1c3648ea
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326725"
---
# <a name="writing-multi-processor-aware-loggers"></a>撰寫能夠辨識多處理器的記錄器
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 雖能夠使用多個處理器來大幅縮短專案建置時間，但同時也增加了建置事件記錄的複雜性。 在單一處理器環境中，事件、訊息、警告和錯誤是以可預測的循序方式傳入記錄器。 不過，在多處理器環境中，不同來源的事件可能會同時或不依順序傳入。 為解決這個問題，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 提供了能夠辨識多處理器的記錄器以及新的記錄模型，可讓您建立自訂的「轉送記錄器」。  
  
## <a name="multi-processor-logging-challenges"></a>多處理器記錄挑戰  
 當您在多處理器或多核心系統中組建一或多個專案時，所有專案的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 組建事件會同時產生。 記錄器可能會同時或不依順序收到大量的事件訊息。 因為 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 記錄器不是專門處理這種情況的，所以記錄器可能不勝負荷，導致組建時間拉長、不正確記錄器輸出，甚至中斷組建。 為解決這些問題，記錄器 (從 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 開始) 可處理不依順序的事件，並將事件與其來源建立相互關聯。  
  
 建立自訂轉送記錄器，甚至可以改善更多的記錄效率。 自訂轉送記錄器可讓您在組建之前只選擇您要監視的事件，以作為篩選。 當您使用自訂轉送記錄器時，不想要的事件不會讓記錄器不勝負荷、導致記錄雜亂，或讓組建時間變慢。  
  
## <a name="multi-processor-logging-models"></a>多處理器記錄模型  
 為解決與多處理器相關的建置問題，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 支援兩種記錄模式，分別為中央和分散式。  
  
### <a name="central-logging-model"></a>集中式記錄模型  
 在集中式記錄模型中，MSBuild.exe 的單一執行個體做為「中央節點」，中央節點的子執行個體 (「次要節點」) 則附加至中央節點，協助它執行組建工作。  
  
 ![中央記錄器模型](../msbuild/media/centralnode.png "CentralNode")  
  
 附加至中央節點的各類記錄器稱為「中央記錄器」。 每個記錄器類型同時只能有一個執行個體附加到中央節點。  
  
 組建時，次要節點會將其組建事件路由至中央節點。 中央節點則將其所有事件，以及次要節點的事件，路由至一或多個附加的中央記錄器。 然後，記錄器根據傳入的資料建立記錄檔。  
  
 雖然中央記錄器只需要實作 <xref:Microsoft.Build.Framework.ILogger>，但建議您一併實作 <xref:Microsoft.Build.Framework.INodeLogger>，以便中央記錄器使用參與組建的節點數目初始化。 引擎初始化記錄器時，<xref:Microsoft.Build.Framework.ILogger.Initialize%2A> 方法的下列多載會叫用。  
  
```csharp
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
 任何預先存在的 <xref:Microsoft.Build.Framework.ILogger> 型記錄器都可當做中央記錄器，附加至組建。 不過，寫入中央記錄器但未明確支援多處理器記錄情況及失序事件，可能會中斷組建或產生無意義的輸出。  
  
### <a name="distributed-logging-model"></a>分散式記錄模型  
 在集中式記錄模型中，傳入訊息流量過多可能會造成中央節點不勝負荷，例如，同時組建許多專案時。 這會造成系統資源壓力並降低組建效能。 為解決這個問題，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 支援分散式記錄模型。  
  
 ![分散式記錄模型](../msbuild/media/distnode.png "DistNode")  
  
 分散式記錄模型可讓您建立轉送記錄器，擴展集中式記錄模型。  
  
#### <a name="forwarding-loggers"></a>轉送記錄器  
 轉送記錄器是次要的輕量型記錄器，有附加至次要節點的事件篩選器，並可從該節點接收傳入的組建事件。 它會篩選傳入的事件，並只將您指定的事件轉送到中央節點。 這會減少傳送到中央節點的訊息流量，改善整體的組建效能。  
  
 使用分散式記錄的方式有兩種，如下所示：  
  
-   自訂預先製作的 <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> 轉送記錄器。  
  
-   撰寫您自己的自訂轉送記錄器。  
  
 您可以修改 ConfigurableForwardingLogger 使符合您的需求。 若要這樣做，請使用 MSBuild.exe 在命令列上呼叫記錄器，並列出您想要記錄器轉送到中央節點的組建事件。  
  
 或者，您也可以建立自訂的轉送記錄器。 建立自訂轉送記錄器，可以微調記錄器的行為。 不過，建立自訂轉送記錄器會比只自訂 ConfigurableForwardingLogger 更為複雜。 如需詳細資訊，請參閱[建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)。  
  
## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>使用 ConfigurableForwardingLogger 進行簡單的分散式記錄  
 若要附加 ConfigurableForwardingLogger 或自訂的轉送記錄器，請在 MSBuild.exe 命令列組建中使用 `/distributedlogger` 參數 (簡寫為 `/dl`)。 用於指定記錄器類型和類別名稱的格式與 `/logger` 參數相同，差異在於分散式記錄器一律有兩個記錄類別，而不是一個：轉送記錄器和集中式記錄器。 以下是如何附加 XMLForwardingLogger 自訂轉送記錄器的範例。  
  
```cmd  
msbuild.exe myproj.proj/distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral  
```  
  
> [!NOTE]
>  `/dl` 參數中必須使用星號 (*) 分隔兩個記錄器名稱。  
  
 使用 ConfigurableForwardingLogger 和使用任何其他記錄器一樣 (如[取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)中所述)，不同之處為附加 ConfigurableForwardingLogger 記錄器，而不是一般的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 記錄器，而且要將您讓 ConfigurableForwardingLogger 傳遞給中央節點的事件，指定為參數。  
  
 例如，如果只想收到組建開始和結束以及發生錯誤的通知，您可以傳遞 `BUILDSTARTEDEVENT`、`BUILDFINISHEDEVENT` 和 `ERROREVENT` 做為參數。 傳遞多個參數時可以分號分隔。 下例示範如何使用 ConfigurableForwardingLogger 只轉送 `BUILDSTARTEDEVENT`、`BUILDFINISHEDEVENT` 和 `ERROREVENT` 事件。  
  
```cmd  
msbuild.exe myproj.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT  
```  
  
 以下是可用的 ConfigurableForwardingLogger 參數清單。  
  
|ConfigurableForwardingLogger 參數|  
|---------------------------------------------|  
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
  
## <a name="see-also"></a>請參閱  
 [建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)