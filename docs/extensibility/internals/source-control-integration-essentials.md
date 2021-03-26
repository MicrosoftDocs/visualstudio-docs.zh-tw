---
title: 原始檔控制整合基本概念 |Microsoft Docs
description: 瞭解 Visual Studio 支援的兩種原始檔控制整合類型：原始檔控制外掛程式和以 VSPackage 為基礎的原始檔控制解決方案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 155e662eae0dda6689a233e31fd62bb72259ae8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069331"
---
# <a name="source-control-integration-essentials"></a>原始檔控制整合的基本資訊
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援兩種類型的原始檔控制整合：提供基本功能的原始檔控制外掛程式，以及使用原始檔控制外掛程式 API 建立的 (先前稱為 MSSCCI API) ，以及以 VSPackage 為基礎的原始檔控制整合解決方案，可提供更強大的功能。

## <a name="source-control-plug-in"></a>原始檔控制外掛程式
 原始檔控制外掛程式會以 DLL 的形式寫入，以執行原始檔控制外掛程式 API。 註冊和原始檔控制整合功能是透過 API 所提供。 這種方法比原始檔控制 VSPackage 更容易執行，而且會 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 針對大部分的原始檔控制作業使用使用者介面 (UI) 。

 若要使用原始檔控制外掛程式 API 來執行原始檔控制外掛程式，請遵循下列步驟：

1. 建立可執行 [原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)中所指定之函式的 DLL。

2. 依照 [如何：安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)所述，建立適當的登錄專案以註冊 DLL。

3. 當原始檔控制介面卡封裝的提示 ([!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 透過原始檔控制外掛程式處理原始檔控制功能的元件時，請建立協助程式 UI 並顯示它) 。

   如需詳細資訊，請參閱 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)。

## <a name="source-control-vspackage"></a>原始檔控制 VSPackage
 原始檔控制 VSPackage 執行可讓您針對原始檔控制 UI 開發自訂的取代 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 這種方法可提供原始檔控制整合的完整控制權，但需要您提供 UI 元素，並執行在外掛程式方法下提供的原始檔控制介面。

 若要執行原始檔控制 VSPackage，您必須：

1. 建立並註冊您自己的原始檔控制 VSPackage （如 [註冊和選取專案](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)所述）。

2. 以您的自訂 UI 取代預設的原始檔控制 UI。 請參閱 [自訂消費者介面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)。

3. 指定要使用的字元，並處理 **方案總管** 的圖像事件。 請參閱圖像 [控制](../../extensibility/internals/glyph-control-source-control-vspackage.md)。

4. 處理查詢編輯和查詢儲存事件，如 [查詢編輯查詢儲存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)所示。

   如需詳細資訊，請參閱 [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。

## <a name="see-also"></a>另請參閱
- [概觀](../../extensibility/internals/source-control-integration-overview.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
