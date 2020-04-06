---
title: 為自動化模型做出貢獻 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d660edc740229c3e91b99e1f59eb37b4e9312098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709262"
---
# <a name="contribute-to-the-automation-model"></a>為自動化模型做出貢獻
Visual Studio 提供了一組用於自定義環境的自動化介面。 自動化模型是使最終使用者能夠創建 Visual Studio 外接程式和擴展的物件模型。

 此外,作為 VSPackage 開發人員,您適合為自動化模型做出貢獻;通過執行此操作,可以使 VSPackage 的最終使用者創建外接程式,並且通常在中使用 VSPackage 時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供一致的用戶體驗。

 為了使最終用戶體驗保持一致,您可以在設計 VSPackage 時遵循一組準則,以便 VSPackage 的自動化[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]模型遵循 中的想法。

## <a name="in-this-section"></a>本節內容
- [自動化模型概述](../../extensibility/internals/automation-model-overview.md)

 將自動化模型定義為控制公共環境主要方面的相關物件組。 這組物件在自動化模型的圖表中繪製。

- [為 VS 套件提供自動化](../../extensibility/internals/providing-automation-for-vspackages.md)

 討論為 VSPackage 提供自動化的兩種主要方法。

- [公開項目物件](../../extensibility/internals/exposing-project-objects.md)

 提供用於創建特定於 VSPackage 物件的分步說明。

- [專案建模](../../extensibility/internals/project-modeling.md)

 解釋為新專案類型創建自動化所需的標準專案物件,並說明專案自動化遵循的路徑。 本主題還提供類的聲明和實現的清單。

- [公開事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 提供為自動化模型創建事件的分步說明。

- [選項頁的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)

 描述如何透過擴充物件來傳回用於支援 **「工具**」功能表上`DTE.Properties`VSPackage 自訂**選項**對話方塊屬性的自動化物件。

- [提供程式碼自動化](../../extensibility/internals/providing-automation-for-code.md)

 說明不需要為代碼創建自動化模型。 但是,本主題中提供了一個連結,該連結提供了代碼模型的有見地資訊。

- [如何:Windows 提供自動化](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 說明,每當您想要在視窗中提供自動化物件,並且環境尚未提供現成的自動化物件時,提供自動化都是一個好主意。 討論工具視窗和文檔視窗的自動化。

- [使用自動化模型](../../extensibility/internals/using-the-automation-model.md)

 提供了兩個代碼示例,顯示自動化消費者如何獲取初始專案自動化物件。

- [設定與選取項目的自動化](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 提供有關配置和選定專案物件的自動化的資訊。

## <a name="reference"></a>參考
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>提供一個程式碼範例,用於顯示 VSPackage 如何參與 DTE 自動化物件模型。 列出參數、返回值和所選備註。
