---
title: 命令設計 |Microsoft Docs
description: 瞭解如何在 Visual Studio 中設計 VSPackage 的命令。 包括、如何指定出現的位置、可用的位置，以及處理方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0acef6dd38238ef58f1dd66f7d8de35318e4ffc6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078925"
---
# <a name="command-design"></a>命令設計
當您將命令新增至 VSPackage 時，您必須指定其出現的位置、可用的位置，以及處理方式。

## <a name="define-commands"></a>定義命令
 若要定義新的命令，請在您的 VSPackage 專案中包含 Visual Studio 的命令資料表 (*. .vsct*) 檔。 如果您已經使用 Visual Studio 套件範本來建立 VSPackage，專案會包含這些檔案的其中一個。 如需詳細資訊，請參閱 [Visual Studio 命令表格 (. .vsct) ](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)檔。

 Visual Studio 會合並找到的所有 *.vsct* 檔案，讓它可以顯示命令。 因為這些檔案與 VSPackage 二進位檔不同，Visual Studio 不需要載入封裝來尋找命令。 如需詳細資訊，請參閱 [Vspackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。

 Visual Studio 使用 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 註冊屬性來定義功能表資源和命令。 如需詳細資訊，請參閱 [命令實行](../../extensibility/internals/command-implementation.md)。

 您可以透過數種不同的方式，在執行時間變更命令。 這些使用者可以顯示、隱藏、啟用或停用。 它們可以顯示不同的文字或圖示，或包含不同的值。 在 Visual Studio 載入您的 VSPackage 之前，可能會先執行許多自訂作業。 如需詳細資訊，請參閱 [Vspackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。

## <a name="command-handlers"></a>命令處理常式
 當您建立命令時，您必須提供事件處理常式來執行命令。 如果使用者選取命令，就必須適當地路由傳送。 路由傳送命令表示將它傳送到正確的 VSPackage 來啟用或停用、隱藏或顯示它，並在使用者選擇執行此動作時執行。 如需詳細資訊，請參閱 [命令路由演算法](../../extensibility/internals/command-routing-algorithm.md)。

## <a name="visual-studio-command-environment"></a>Visual Studio 命令環境
 Visual Studio 可以裝載任意數量的 Vspackage，而且每個都可以提供自己的命令集。 環境只會顯示適用于目前工作的命令。 如需詳細資訊，請參閱 [命令可用性](../../extensibility/internals/command-availability.md) 和 [選取專案內容物件](../../extensibility/internals/selection-context-objects.md)。

 定義新命令、功能表、工具列或快捷方式功能表的 VSPackage，會透過參考原生或 managed 元件中資源的登錄專案，在安裝時提供其命令資訊給 Visual Studio。 然後，每個資源都會參考二進位資料資源 (*. cto*) 檔案，此檔案會在您編譯 Visual Studio 命令資料表 (*. .vsct*) 檔時產生。 這可讓 Visual Studio 提供合併的命令集、功能表和工具列，而不必載入每個已安裝的 VSPackage。

### <a name="command-organization"></a>命令組織
 環境依群組、優先順序和功能表來定位命令。

- 群組是相關命令的邏輯集合，例如 **剪** 下、 **複製** 和 **貼** 上命令群組。 群組是出現在功能表上的命令。

- 優先權決定群組中個別命令出現在功能表上的順序。

- 功能表可作為群組的容器。

  環境會預先定義一些命令、群組和功能表。 如需詳細資訊，請參閱 [預設的命令、群組和工具列位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)。

  您可以將命令指派給主要群組。 主要群組會在主功能表結構和 [ **自訂** ] 對話方塊中控制命令的位置。 命令可出現在多個群組中;例如，命令可以位於主功能表、快捷方式功能表和工具列上。 如需詳細資訊，請參閱 [Vspackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)。

### <a name="command-routing"></a>命令路由
 針對 Vspackage 叫用和路由命令的程式，與在物件實例上呼叫方法的進程不同。

 環境會依序將命令從最內層的 (本機) 命令內容（根據目前的選取範圍）路由到最外層的 (全域) 內容。 可以執行此命令的第一個內容是處理它的內容。 如需詳細資訊，請參閱 [命令路由演算法](../../extensibility/internals/command-routing-algorithm.md)。

 在大部分的情況下，環境會使用介面來處理命令 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。 由於命令路由配置可讓許多不同的物件處理命令，因此 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 可由任意數目的物件來執行，這些物件包括 Microsoft ActiveX 控制項、視窗視圖執行、檔物件、專案階層和 VSPackage 物件本身 (用於全域命令) 。 在某些特殊情況下（例如，在階層中路由傳送命令），必須實作為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 介面。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[命令執行](../../extensibility/internals/command-implementation.md)|描述如何在 VSPackage 中執行命令。|
|[命令可用性](../../extensibility/internals/command-availability.md)|描述 Visual Studio 內容如何判斷哪些命令可供使用。|
|[命令路由演算法](../../extensibility/internals/command-routing-algorithm.md)|描述 Visual Studio 命令路由架構如何讓命令由不同的 Vspackage 來處理。|
|[命令放置指導方針](../../extensibility/internals/command-placement-guidelines.md)|建議在 Visual Studio 環境中放置命令的方式。|
|[Vspackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|描述 Vspackage 如何充分利用 Visual Studio 的命令架構。|
|[預設命令、群組和工具列位置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|描述 Vspackage 如何充分利用 Visual Studio 中包含的命令。|
|[管理 VSPackages](../../extensibility/managing-vspackages.md)|描述 Visual Studio 如何載入 Vspackage。|
|[Visual Studio 命令表格 (. .vsct) 檔](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|提供 XML *.vsct* 檔案的相關資訊，這些檔案可用來描述 vspackage 中命令的版面配置和外觀。|
