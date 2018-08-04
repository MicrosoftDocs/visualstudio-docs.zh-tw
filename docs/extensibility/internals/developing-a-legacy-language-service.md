---
title: 開發舊版語言服務 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d92c07742dcc4433aa96071d655f58d938a1f80
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497826"
---
# <a name="develop-a-legacy-language-service"></a>開發舊版語言服務
這個區段會連結至主題可協助您建立舊版語言服務。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解實作語言服務的新方式，請參閱[編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="in-this-section"></a>本節內容  
 [舊版語言服務的模型](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 提供的最小語言服務模型[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]核心編輯器。 您可以使用此模型做為指南，來建立您自己的語言服務。  
  
 [舊版語言服務介面](../../extensibility/internals/legacy-language-service-interfaces.md)  
 討論實作語言服務所需的物件，並提供您可用來提供語法醒目提示、 方法的資料，以及其他功能的其他物件的清單。  
  
 [攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 描述如何插入截距，命令文字 檢視會處理的語言服務中的命令篩選器。  
  
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 提供如何註冊您的語言服務使用的相關資訊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [語言服務支援偵錯](../../extensibility/internals/language-service-support-for-debugging.md)  
 描述如何語言服務可以提供功能，可支援偵錯工具。  
  
 [檢查清單： 建立舊版語言服務](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 提供逐步指示來建立及整合核心編輯器 」 的語言服務。  
  
## <a name="related-sections"></a>相關章節  
 [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 討論如何實作語法反白顯示您的語言服務中。  
  
 [舊版語言服務中的陳述式完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 討論陳述式完成時，處理程序的語言服務可協助使用者完成語言關鍵字或啟動後輸入的項目。  
  
 [舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 描述如何為多載函式和方法提供方法提示。  
  
 [如何： 隱藏的文字提供舊版語言服務中支援](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 說明隱藏的文字區域的目的，並提供有關如何實作在隱藏的文字區域的指示。  
  
 [如何： 提供展開大綱的支援，在舊版語言服務](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 說明擴充大綱的支援，您只能支援的語言的兩個選項*摺疊至定義*命令。