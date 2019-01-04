---
title: 實作舊版語言服務 1 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3218a8cf1c61fb9b88520702a953f2288e19b3c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855883"
---
# <a name="implementing-a-legacy-language-service"></a>實作舊版語言服務
您可以使用在 managed 的 package framework (MPF) 類別來實作舊版語言服務，可支援各種不同的功能，例如語法反白顯示、 括號對稱和 IntelliSense 完成。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解實作語言服務的新方式，請參閱[編輯器和語言服務延伸模組](../../extensibility/editor-and-language-service-extensions.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="in-this-section"></a>本節內容  
 [舊版語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)  
 MPF 中支援的語言服務功能的概觀。  
  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 描述使用 MPF 實作語言服務的必要條件。  
  
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 描述的步驟，才能註冊使用 MPF 型語言服務[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 描述使用 MPF 實作的語言服務的所有功能所需的兩個剖析器。  
  
 [逐步解說：建立舊版語言服務](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 提供在 VSPackage 中實作的 MPF 語言服務所需的基本步驟。  
  
 [逐步解說：取得一份已安裝的程式碼片段 （舊版實作）](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 示範擷取一份已安裝的程式碼片段的技術。  
  
 [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)  
 提供主題的連結，該功能必須使用 MPF 實作的語言服務的所有功能的詳細資料。