---
title: 傳統語言服務功能1 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0be7cb4401792b30eac595faf64162dc375dbb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707391"
---
# <a name="legacy-language-service-features"></a>舊版語言服務功能
託管包框架 (MPF) 語言服務可以支援一個或[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]多個 功能,如語法突出顯示、IntelliSense 和斷點驗證。 每個功能都可以獨立於其他功能實現,但除了語法突出顯示(只需要掃描器)外,所有功能都需要解析器和掃描器。

## <a name="in-this-section"></a>本節內容
- [舊版語言服務中的括號對稱](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 描述支持語言對匹配(也稱為大括弧匹配)所需的內容。

- [在舊版語言服務中將程式碼設為註解](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 描述支持註釋和取消註釋所選代碼所需的內容。

- [舊版語言服務中的自訂文件屬性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 描述支援嵌入在源檔中的文件屬性所需的內容。

- [在舊版語言服務中製作大綱](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 描述通過實施隱藏區域來支援大綱的內容。

- [在舊版語言服務中將程式碼重新格式化](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 描述支援重新格式化代碼所需的內容。

- [舊版語言服務中對程式碼片段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 描述支援代碼段所需的內容,這些代碼段是插入並可編輯的代碼段。

- [舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 描述在鍵入方法時支援 IntelliSense 參數資訊操作以顯示方法簽名所需的內容。

- [舊版語言服務中的快速諮詢](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 描述支援 IntelliSense 快速資訊操作以顯示有關識別碼資訊所需的內容。

- [舊版語言服務中的成員完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 描述支援從清單中選擇命名空間成員所需的「IntelliSense 成員完成」操作所需的內容。

- [舊版語言服務中的文字自動完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 描述支援「IntelliSense 完整字」操作以完成部分鍵入的單詞所需的內容。

- [舊版語言服務中對自動變數視窗的支援](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 描述在除錯時,語言服務可以採取哪些功能來支援**自動視窗**。

- [舊版語言服務中對巡覽列的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 描述如何使用編輯器檢視頂部的**導航列**向該檢視中顯示的檔中的任何類型的或成員提供快速導航。

- [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 描述支援原始碼的語法突出顯示所需的內容。

- [在舊版語言服務中驗證中斷點](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 描述語言服務可以做些什麼來支持驗證調試器外的斷點。

## <a name="related-sections"></a>相關章節
- [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 描述實現使用託管包框架的語言服務的所有功能所需的解析器和掃描器。

- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 描述使用 MPF 實現語言服務所需的內容。

- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)

 描述向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]註冊基於 MPF 的語言服務所需的步驟。

- [Using IntelliSense](../../ide/using-intellisense.md)

 解釋 IntelliSense 如何讓語言參考易於訪問。

- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 提供有關如何使用託管包框架 (MPF) 在託管代碼中實現全功能語言服務的資訊。
