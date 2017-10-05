---
title: "在多處理器環境中的記錄 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: e78d6c35fa294d2f1a39c91af5e278e9e4519d2d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="logging-in-a-multi-processor-environment"></a>在多處理器環境中記錄
MSBuild 雖能夠使用多個處理器來大幅縮短專案建置時間，但同時也增加了記錄的複雜性。 在單一處理器環境中，記錄器可處理傳入的事件、 訊息、 警告和錯誤可預測的循序的方式。 不過，在多處理器環境中，從數個來源的事件可能會同時或不依順序到達。 MSBuild 提供新多處理器的記錄器，並讓您建立自訂 「 轉送記錄器 」。  
  
## <a name="logging-multiple-processor-builds"></a>記錄多處理器建置  
 當您在多處理器或多核心系統中建置一個或多個專案時，所有專案的 MSBuild 建置事件會同時產生。 同時或不依順序收到大量的事件資料可能會到達記錄器。 這可能記錄器不勝負荷，而且會導致建置時間拉長、 不正確記錄器輸出或甚至中斷的建置。 若要解決這些問題，MSBuild 記錄器可以處理序列出事件，並將建立相互關聯事件及其來源。  
  
 您可以改善記錄更多藉由建立自訂轉送記錄器的效率。 自訂轉送記錄器做為篩選條件，可讓您選擇在建置之前您要監視的事件。 當您使用自訂轉送記錄器時，不想要的事件請勿記錄器不勝負荷、 充斥記錄或速度很慢的建置時間。  
  
### <a name="central-logging-model"></a>集中式記錄模型  
 多處理器的組建，MSBuild 會使用 「 中央記錄模型 」。 在集中式記錄模型中，執行個體的 MSBuild.exe 做為主要建置程序或 「 中央節點 」。 MSBuild.exe 或 「 次要節點 」，第二個執行個體附加至集中的節點。 任何 ILogger 為基礎的記錄器連接到中央的節點稱為 「 中央記錄器 」 和記錄器連接到次要節點稱為 「 次要記錄器 」。  
  
 當組建發生時，次要記錄器其事件將流量路由至中央記錄器。 數個次要節點上不會產生事件，因為資料會同時抵達的中央節點，但交錯。 若要解決事件對專案和事件的目標參考，事件引數，包括其他建置事件內容資訊。  
  
 雖然只有<xref:Microsoft.Build.Framework.ILogger>是才能實作中央記錄器，我們建議您一併實作<xref:Microsoft.Build.Framework.INodeLogger>如果您想中央記錄器初始化參與在組建中的節點數目。 下列多載<xref:Microsoft.Build.Framework.ILogger.Initialize%2A>引擎初始化記錄器時，會叫用方法：  
  
```csharp
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### <a name="distributed-logging-model"></a>分散式記錄模型  
 在集中式記錄模型中，太多傳入的訊息傳輸，例如當許多建置專案，可能會淹沒的中央節點造成系統負擔並降低建置效能。  
  
 若要減少此問題，MSBuild 也可讓 「 分散式的記錄模型 」，可讓您建立轉送記錄器延伸集中式記錄模型。 轉送記錄器連接到次要節點，並從該節點中接收傳入的建置事件。 轉送記錄器就如同一般的記錄器，不同之處在於它可以篩選的事件，並將所需的中央節點。 這可減少在集中的節點上的訊息流量，並因此可讓更佳的效能。  
  
 您可以實作來建立轉送記錄器<xref:Microsoft.Build.Framework.IForwardingLogger>介面衍生自<xref:Microsoft.Build.Framework.ILogger>。 介面會定義如下：  
  
```csharp
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 若要轉遞轉送記錄器中的事件，呼叫<xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A>方法<xref:Microsoft.Build.Framework.IEventRedirector>介面。 傳遞適當<xref:Microsoft.Build.Framework.BuildEventArgs>，或衍生作品，做為參數。  
  
 如需詳細資訊，請參閱[建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)。  
  
### <a name="attaching-a-distributed-logger"></a>附加分散式的記錄器  
 若要附加命令列建置分散式的記錄器，請使用`/distributedlogger`(或者，`/dl`簡稱) 切換。 指定的記錄器類型和類別名稱的格式會與相同`/logger`切換，不同之處在於兩個記錄類別包含分散式的記錄器： 轉送記錄器和中央記錄器。 以下是範例附加分散式的記錄器：  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 星號 （*） 區隔中的兩個記錄器名稱`/dl`切換。  
  
## <a name="see-also"></a>另請參閱  
 [組建記錄器](../msbuild/build-loggers.md)   
 [建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)
