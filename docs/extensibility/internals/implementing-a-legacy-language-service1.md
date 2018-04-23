---
title: 實作舊版語言 Service1 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0486b8ad035d64f542d48f1e304413780958d90c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-a-legacy-language-service"></a>實作舊版語言服務
您可以使用 managed 的 package framework (MPF) 中的類別來實作可支援各種不同的功能，舊版語言服務，例如語法反白顯示、 括號對稱和 IntelliSense 完成。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要了解有關實作語言服務的新方法的詳細資訊，請參閱[編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="in-this-section"></a>本節內容  
 [舊版語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)  
 MPF 中支援的語言服務功能的概觀。  
  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 描述使用 MPF 實作語言服務的必要條件。  
  
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 描述使用 MPF 為基礎的語言服務登錄所需的步驟[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 描述使用 MPF 實作語言服務的所有功能所需的兩個分析。  
  
 [逐步解說：建立舊版語言服務](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 提供在 VSPackage 中實作的 MPF 語言服務所需的基本步驟。  
  
 [逐步解說︰取得已安裝程式碼片段 (舊版實作) 的清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 示範的技術，擷取已安裝的程式碼片段的清單。  
  
 [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)  
 提供主題的連結所必須完成的工作，以使用 MPF 實作語言服務的所有功能的詳細資料。