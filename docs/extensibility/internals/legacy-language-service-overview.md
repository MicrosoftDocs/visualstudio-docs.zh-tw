---
title: 傳統語言服務概述 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed653ec200063e72434fc758c7920e6caabafe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707352"
---
# <a name="legacy-language-service-overview"></a>舊版語言服務概觀
語言服務提供編輯器支援,使您能夠實現某些[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]功能。 託管包框架 (MPF) 語言服務類提供對常用功能的完全支援,並支援其他功能。

## <a name="fully-supported-features-in-the-mpf"></a>強積金中完全支援的功能
 MPF 語言服務類別支援以下功能:

- 語法醒目提示

- 大綱

- 註解程式

- 括號對稱

- 程式碼片段

- 自訂文件屬性

- IntelliSense 參數資訊

- 感知快速資訊

- IntelliSense 會員完成

- IntelliSense 字完成

## <a name="partially-supported-features-in-the-mpf"></a>強積金中部分支援的功能
 MPF 僅對以下功能提供部分支援。 這意味著您必須實現 MPF 調用的方法。

- 重新格式化代碼。 提供實現重新格式化的代碼。

- 通過標識有效的代碼範圍驗證斷點。 提供標識代碼範圍的代碼。

- 支援調試器**自動**視窗以顯示變數。 提供確定在視窗中顯示內容的代碼。

- 支持**導航列**,用於類型和成員之間的快速導航。 實現並返回一個幫助程式類,該類填充**導航欄**組合框中的清單。

## <a name="implementation"></a>實作
 您必須完成幾個步驟,以實現語言服務本身和要支援的語言服務功能。 這些步驟在以下主題中討論:

- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [舊版語言服務中的括號對稱](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [在舊版語言服務中製作大綱](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [在舊版語言服務中將程式碼設為註解](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [在舊版語言服務中將程式碼重新格式化](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [舊版語言服務中的自訂文件屬性](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [舊版語言服務中對程式碼片段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [舊版語言服務中對巡覽列的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [舊版語言服務中的文字自動完成](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [舊版語言服務中的成員完成](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [舊版語言服務中的快速諮詢](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [舊版語言服務中對自動變數視窗的支援](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [在舊版語言服務中驗證中斷點](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>另請參閱
- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [舊版語言服務的擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)
