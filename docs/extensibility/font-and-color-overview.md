---
title: 字型和色彩概觀 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 790a9f8bbed02a5135897f33db7fac1af3ad89d9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342569"
---
# <a name="font-and-color-overview"></a>字型和色彩的概觀
本主題討論中的文字字型和色彩設定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。 它也會介紹的概念類別和顯示項目，並說明如何在 Vspackage 和核心編輯器使用文字屬性。

## <a name="the-fonts-and-colors-property-page"></a>字型和色彩屬性頁面
 您可以管理屬性中顯示的文字[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]經由整合式的開發環境 (IDE)**字型和色彩**屬性頁。 若要尋找**字型和色彩**] 屬性頁面上**工具**功能表上，按一下 [**選項**。 依序展開**環境**，然後按一下**字型和色彩**。

## <a name="categories-and-display-items"></a>類別和顯示項目
 字型和色彩區分成**分類**並**顯示項目**。

- A**分類**是邏輯或功能的容器數目**顯示項目**。

   一份**分類**處於**顯示設定**下拉式清單方塊**字型和色彩**屬性頁。

- A**顯示項目**是妥善定義的文字實體，例如註解、 字串或控制結構，會以色彩標示時顯示。

  每個**顯示項目**內都唯一定義**分類**包含它。 因此，有一個以上**分類**可以有**顯示項目**具有相同名稱。

## <a name="vspackage-control-of-fonts-and-colors"></a>VSPackage 控制字型和色彩
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]可讓 Vspackage 來：

- 定義字型和色彩**分類**。

- 指定的字型和色彩來呈現**顯示的項目**。

- 互動**字型和色彩**屬性頁。

- 彙總的多個**分類**分組。

- 保留預設設定中的變更。

  有兩種方式進行互動中的字型和色彩選取[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]。

- 其中一種方式指*語法著色*。 它由自訂現有的 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]實作語言服務，並建立來源編輯器的編輯器。

   只有一個**分類**支援這項機制，也就是，則**文字編輯器**。

- 較通用的替代方式支援所有其他**分類**和原始檔編輯器時顯示文字以外的使用者介面元件。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>。

## <a name="core-editor-text-settings"></a>核心編輯器文字設定
 語言服務物件的核心編輯器的字型和色彩設定所控管**文字 EditorCategory**中找到**顯示設定**下拉式清單方塊的**字型和色彩**屬性頁。

 當使用編輯器，您應該使用特殊的字型和色彩控制機制，語言服務提供給控制項，並擴充**文字編輯器**設定。 此機制稱為*語法著色*，並提供：

- 簡化的技術來管理的字型和色彩的顯示項目。

   如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 與 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>。

- 定義完善且經過最佳化的顏色標示的機制。

   如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>。

- 能夠同時使用內建的顯示項目，從**文字 EditorCategory**和延伸。

   如需詳細資訊，請參閱[如何：使用內建可設定色彩的項目](../extensibility/internals/how-to-use-built-in-colorable-items.md)並[自訂色彩項目](../extensibility/internals/custom-colorable-items.md)。

- 自動的持續性的目前狀態的兩個內建和自訂顯示的項目**文字編輯器**類別目錄。

  如需有關語法著色，請參閱[舊版語言服務中的語法著色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。

## <a name="see-also"></a>另請參閱
- [在編輯器中的舊版介面](../extensibility/legacy-interfaces-in-the-editor.md)
- [舊版語言服務中的語法著色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)