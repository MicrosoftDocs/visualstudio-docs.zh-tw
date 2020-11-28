---
title: 參與 Automation 模型 |Microsoft Docs
description: 瞭解如何在設計 VSPackage 時遵循一組指導方針來參與 Visual Studio automation 模型。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ab43da108a8d4a3339c54973f60bf1bef6a74780
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305604"
---
# <a name="contribute-to-the-automation-model"></a>參與 automation 模型
Visual Studio 提供一組自動化介面來自訂環境。 Automation 模型是物件模型，可讓使用者建立 Visual Studio 的增益集和延伸模組。

 此外，它也適合做為 VSPackage 開發人員，以提供給 automation 模型;如此一來，您就可以讓 VSPackage 的終端使用者建立增益集，而且通常會在使用您的 VSPackage 時提供一致的使用者模型體驗 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

 若要讓終端使用者體驗保持一致，您可以在設計 VSPackage 時遵循一組指導方針，讓 VSPackage 的自動化模型遵循中的想法 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

## <a name="in-this-section"></a>本節內容
- [Automation 模型總覽](../../extensibility/internals/automation-model-overview.md)

 將 automation 模型定義為控制常見環境之主要 facet 的相關物件群組。 這組物件會以自動化模型的圖表來圖解。

- [為 Vspackage 提供自動化](../../extensibility/internals/providing-automation-for-vspackages.md)

 討論為 VSPackage 提供自動化的兩個主要方式。

- [公開專案物件](../../extensibility/internals/exposing-project-objects.md)

 提供建立 VSPackage 特定物件的逐步指示。

- [專案模型](../../extensibility/internals/project-modeling.md)

 說明為新的專案類型建立自動化所需的標準專案物件，並說明專案自動化遵循的路徑。 本主題也提供類別的宣告和執行清單。

- [公開事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 提供逐步指示，說明如何為您的 automation 模型建立事件。

- [選項頁的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)

 描述如何藉由擴充物件，在 **工具** 功能表上，傳回 VSPackage 的 [自訂 **選項**] 對話方塊支援屬性的自動化物件 `DTE.Properties` 。

- [為程式碼提供自動化](../../extensibility/internals/providing-automation-for-code.md)

 說明不需要為您的程式碼建立 automation 模型。 不過，本主題提供的連結可提供程式碼模型的相關資訊。

- [如何：為 Windows 提供自動化](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 說明當您想要讓自動化物件可在視窗上使用，且環境尚未提供現成的 automation 物件時，提供自動化是很好的想法。 討論工具視窗和文件視窗的自動化。

- [使用 automation 模型](../../extensibility/internals/using-the-automation-model.md)

 提供兩個程式碼範例，示範 automation 取用者如何取得初始專案自動化物件。

- [Configuration 和 SelectedItem 物件的自動化](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 提供 Configuration 和 SelectedItems 物件自動化的相關資訊。

## <a name="reference"></a>參考
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 提供的程式碼範例會顯示 VSPackage 如何參與 DTE automation 物件模型。 列出參數、傳回值和選取的備註。
