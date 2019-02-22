---
title: 原始檔控制整合的基本資訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16c785534b843977f28c9a1383ac93f33e216947
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619481"
---
# <a name="source-control-integration-essentials"></a>原始檔控制整合的基本資訊
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援兩種類型的原始檔控制整合： 原始檔控制外掛程式提供基本功能，使用原始檔控制外掛程式 API （前身為 MSSCCI API） 和 VSPackage 型原始檔控制整合解決方案建置，提供更強大的功能。

## <a name="source-control-plug-in"></a>原始檔控制外掛程式
 原始檔控制外掛程式會寫入做為實作原始檔控制外掛程式 API 的 DLL。 透過 API 提供註冊和原始檔控制整合功能。 這個方法會比原始檔控制 VSPackage，容易實作，並使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]大部分的原始檔控制作業的使用者介面 (UI)。

 若要實作原始檔控制外掛程式使用原始檔控制外掛程式 API，請遵循下列步驟：

1. 建立一個實作中指定的函式的 DLL[原始檔控制外掛程式](../../extensibility/source-control-plug-ins.md)。

2. 中所述，藉由適當的登錄項目中，登錄 DLL [How to:安裝原始檔控制外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)。

3. 建立協助程式 UI，並顯示原始檔控制配接器套件出現提示時 ([!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]會處理透過原始檔控制外掛程式的原始檔控制功能的元件)。

   如需詳細資訊，請參閱 <<c0> [ 建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)。

## <a name="source-control-vspackage"></a>原始檔控制 VSPackage
 原始檔控制 VSPackage 實作可讓您開發自訂的取代[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]原始檔控制 UI。 這種方法可讓您完整控制原始檔控制整合，但它會要求您提供的 UI 項目，並實作來源控制介面，否則會在可提供的外掛程式方法。

 若要實作原始檔控制 VSPackage，您必須：

1. 建立並註冊您自己的原始檔控制 VSPackage，如中所述[註冊和選取](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)。

2. 取代您自訂的 UI 中的預設原始檔控制 UI。 請參閱[自訂使用者介面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)。

3. 指定使用，並處理字符**方案總管 中**圖像 （glyph） 的事件。 請參閱[字符控制](../../extensibility/internals/glyph-control-source-control-vspackage.md)。

4. 處理查詢編輯並查詢儲存的事件，如中所示[查詢編輯查詢儲存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)。

   如需詳細資訊，請參閱 <<c0> [ 建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)。

## <a name="see-also"></a>另請參閱
- [概觀](../../extensibility/internals/source-control-integration-overview.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)