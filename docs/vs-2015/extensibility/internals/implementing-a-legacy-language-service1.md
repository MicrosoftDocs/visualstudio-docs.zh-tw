---
title: 執行舊版語言 Service1 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20493991d8e0740ca045f041e2ba94cf3735ad1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839075"
---
# <a name="implementing-a-legacy-language-service"></a>實作舊版語言服務
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您可以使用 managed package framework 中的類別 (MPF) 來執行支援各種功能的舊版語言服務，例如語法醒目提示、括弧對稱和 IntelliSense 完成。  
  
 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解如何執行語言服務的新方法，請參閱 [編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。  
  
## <a name="in-this-section"></a>本節內容  
 [舊版語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)  
 支援 MPF 的語言服務功能。  
  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 描述使用 MPF 來執行語言服務所需的內容。  
  
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 描述向註冊以 MPF 為基礎之語言服務的必要步驟 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
 [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 描述使用 MPF 來執行語言服務的所有功能所需的兩個剖析器。  
  
 [逐步解說：建立舊版語言服務](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 提供在 VSPackage 中執行 MPF 語言服務所需的基本步驟。  
  
 [逐步解說：取得已安裝的程式碼片段 (舊版實作) 清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 示範抓取已安裝程式碼片段清單的技巧。  
  
 [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)  
 提供主題的連結，這些主題詳細說明必須完成才能使用 MPF 來執行語言服務的所有功能。
