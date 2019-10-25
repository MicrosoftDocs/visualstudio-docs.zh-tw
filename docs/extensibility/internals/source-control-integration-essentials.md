---
title: 原始檔控制整合基本概念 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcce3d8fdcc1c99c9b91bfebec572033ff3beb1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723469"
---
# <a name="source-control-integration-essentials"></a>原始檔控制整合的基本資訊
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援兩種類型的原始檔控制整合：提供基本功能並使用原始檔控制外掛程式 API （先前稱為 MSSCCI API）建立的原始檔控制外掛程式，以及以 VSPackage 為基礎的原始檔控制整合解決方案這可提供更強大的功能。

## <a name="source-control-plug-in"></a>原始檔控制外掛程式
 原始檔控制外掛程式會以 DLL 的形式寫入，以執行原始檔控制外掛程式 API。 註冊和原始檔控制整合功能是透過 API 提供。 這個方法比原始檔控制 VSPackage 更容易執行，而且它會使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的使用者介面（UI）來進行大部分的原始檔控制作業。

 若要使用原始檔控制外掛程式 API 來執行原始檔控制外掛程式，請遵循下列步驟：

1. 建立 DLL，以執行[原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)中指定的函式。

2. 藉由建立適當的登錄專案來註冊 DLL，如[如何：安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)中所述。

3. 建立 helper UI，並在原始檔控制介面卡套件（透過原始檔控制外掛程式處理原始檔控制功能的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 元件）提示時顯示它。

   如需詳細資訊，請參閱[建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)。

## <a name="source-control-vspackage"></a>原始檔控制 VSPackage
 原始檔控制 VSPackage 的執行可讓您為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 原始檔控制 UI 開發自訂的取代。 這種方法可讓您完整控制原始檔控制整合，但它需要您提供 UI 元素，並實作為外掛程式方法所提供的原始檔控制介面。

 若要執行原始檔控制 VSPackage，您必須：

1. 建立並註冊您自己的原始檔控制 VSPackage，如[註冊和選取](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)中所述。

2. 將預設的原始檔控制 UI 取代為您的自訂 UI。 請參閱[自訂使用者介面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)。

3. 指定要使用的字元，並處理**方案總管**的圖像事件。 請參閱[字型控制項](../../extensibility/internals/glyph-control-source-control-vspackage.md)。

4. 處理查詢編輯和查詢儲存事件，如[查詢編輯查詢儲存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)中所示。

   如需詳細資訊，請參閱[建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。

## <a name="see-also"></a>請參閱
- [概觀](../../extensibility/internals/source-control-integration-overview.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)