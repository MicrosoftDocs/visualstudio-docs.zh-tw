---
title: 實現傳統語言服務1 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3805e49ffa83f7dea2ee58ef36e1bc8e48b1eaa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707691"
---
# <a name="implementing-a-legacy-language-service"></a>實作舊版語言服務
您可以使用託管包框架 (MPF) 中的類來實現支援各種功能的傳統語言服務,例如語法突出顯示、大括弧匹配和 IntelliSense 完成。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解有關實現語言服務的新方法的詳細資訊,請參閱[編輯器和語言服務擴展](../../extensibility/editor-and-language-service-extensions.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="in-this-section"></a>本節內容
- [舊版語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)

 MPF 支援的語言服務功能概述。

- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 描述使用 MPF 實現語言服務所需的內容。

- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)

 描述向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]註冊基於 MPF 的語言服務所需的步驟。

- [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 描述使用 MPF 實現語言服務的所有功能所需的兩個解析器。

- [逐步解說：建立舊版語言服務](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 提供在 VS 套件中實現 MPF 語言服務所需的基本步驟。

- [逐步解說︰取得已安裝程式碼片段 (舊版實作) 的清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 演示檢索已安裝代碼段清單的技術。

- [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)

 提供指向主題的連結,詳細說明使用 MPF 實現語言服務的所有功能必須做什麼。
