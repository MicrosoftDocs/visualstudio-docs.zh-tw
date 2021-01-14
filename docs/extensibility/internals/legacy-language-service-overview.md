---
title: 舊版語言服務總覽 |Microsoft Docs
description: 瞭解 Visual Studio 中的舊版語言服務，以及受管理套件架構 (MPF) 語言服務類別所支援的功能。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c1ec349e38acbdb0271ecfb0c081b4f1aadadcd9
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204939"
---
# <a name="legacy-language-service-overview"></a>舊版語言服務概觀
語言服務提供編輯器支援，可讓您執行特定 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 功能。 受管理的封裝架構 (MPF) 語言服務類別可提供對常用功能的完整支援，以及其他功能的部分支援。

## <a name="fully-supported-features-in-the-mpf"></a>MPF 中完全支援的功能
 MPF 語言服務類別支援下列功能：

- 語法醒目提示

- 大綱

- 程式碼的批註區塊

- 括號對稱

- 程式碼片段

- 自訂文件屬性

- IntelliSense 參數資訊

- IntelliSense 快速資訊

- IntelliSense 成員完成

- IntelliSense 單字完成

## <a name="partially-supported-features-in-the-mpf"></a>MPF 中部分支援的功能
 MPF 僅提供下列功能的部分支援。 這表示您必須執行 MPF 所呼叫的方法。

- 重新格式化程式碼。 您提供可執行重新格式化的程式碼。

- 藉由識別有效的程式碼範圍來驗證中斷點。 您會提供可識別程式碼範圍的程式碼。

- 支援顯示變數 **的偵錯工具** 自動變數視窗。 您可以提供程式碼來決定要在視窗中顯示的內容。

- 支援在類型和成員之間快速流覽的 **導覽** 列。 您會執行並傳回 helper 類別，以填入 **巡覽列** 下拉式方塊中的清單。

## <a name="implementation"></a>實作
 您必須完成幾個步驟，才能執行語言服務本身，以及您想要支援的語言服務功能。 這些步驟將在下列主題中討論：

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

## <a name="see-also"></a>請參閱
- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [舊版語言服務的擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)
