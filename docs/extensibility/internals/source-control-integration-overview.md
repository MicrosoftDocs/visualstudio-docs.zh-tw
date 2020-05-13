---
title: 源代碼管理集成概述 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d80363286f5f0cac9a5ceb2e8ac9d20345df9e6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705116"
---
# <a name="source-control-integration-overview"></a>原始檔控制整合概觀
本節比較了集成到 Visual Studio 原始程式碼管理中的兩種方法;源控元件外掛程式和 VSPackage,提供原始碼管理解決方案並突出顯示新的原始程式碼管理功能。 Visual Studio 允許在原始碼管理 VS 包和原始程式碼管理外掛程式之間手動切換,以及基於解決方案的自動切換。

## <a name="source-control-integration"></a>原始檔控制整合
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援兩種類型的原始程式碼管理整合選項。 在所有版本中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)],您仍可以基於原始程式碼管理外掛程式 API(以前也稱為 MSSCCI API)整合外掛程式,該 API 在使用 Visual Studio 原始碼管理使用者介面 (UI) 時提供基本的原始程式碼管理功能。 另一方面,原始程式碼管理 VSPackage 提供了一種[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]新的深度整合路徑,適用於原始程式碼管理整合,需要原始程式碼管理模型的高度複雜性和自主性。

 ![原始程式碼管理概述](../../extensibility/internals/media/sourcectnrloverview.gif "源Ctnrl概述")

## <a name="source-control-plug-in"></a>原始程式管理外掛程式
 所有版本的 Visual Studio 都支援原始程式碼管理外掛程式 API 規範版本 1.2 作為整合路徑。 源代碼管理外掛程式實現者編寫一個 DLL,該 DLL 實現原始碼管理外掛程式 API 功能,用於原始程式碼管理整合和註冊,如[創建原始碼管理外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)中所述。 在此方法中,集成開發環境 (IDE)[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用 UI 用於對話方塊,例如簽入、簽出、工具/選項屬性頁、工具列和原始程式碼管理字形。 嚴格遵守原始程式碼管理外掛程式 API 可確保輕鬆整合到 Visual Studio 中,並為使用者提供無故障體驗。 這意味著原始程式碼管理外掛程式必須實現 API 中詳述的大多數功能和回調。

 要使用原始碼管理外掛程式 API 實作原始程式,請按照以下步驟操作:

1. 建立實現[原始程式碼管理外掛程式](../../extensibility/source-control-plug-ins.md)中指定的函數的 DLL。

2. 通過建立適當的註冊表項註冊 DLL([在「如何:安裝原始程式碼管理外掛程式」](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)中所述)。

3. 建立說明程式 UI 並在由源碼管理介面管理卡程式(透過源碼管理外掛程式處理原始碼管理功能的 Visual Studio 元件)提示時顯示

   為了回應原始程式碼管理命令,Visual Studio IDE 為基本操作提供了標準 UI,然後透過原始程式碼管理外掛程式 API 中定義的函數將資訊傳遞給原始程式碼管理外掛程式。 對於高級選項,可以調用原始程式碼管理外掛程式來顯示其自己的 UI,例如,流覽原始程式碼管理的專案。 這意味著在處理原始程式碼管理時,使用者可能會看到兩種可能不同的 UI 樣式:Visual Studio 提供的 UI 和原始程式碼管理外掛程式提供的 UI。 這在高級原始程式碼管理操作中最為明顯。

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>實現原始碼管理外掛程式的缺點

- 對於高級功能,使用者可能會看到兩種不同的介面樣式,從而導致可能的混亂。

- 原始程式碼管理外掛程式僅限於原始程式碼管理外掛程式 API 隱含的原始程式碼管理模型。

- 對於某些原始程式碼管理方案,原始程式碼管理外掛程式 API 可能過於嚴格。

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>實現原始碼管理外掛程式的優勢

- Visual Studio 為所有基本原始碼管理操作提供所有 UI,以便原始程式碼管理外掛程式不必實現潛在的複雜 UI。

- 由於 API 嚴格,原始程式碼管理外掛程式可以輕鬆地與外部原始程式碼管理程式互動,以提供更廣泛的功能;Visual Studio 不太關心原始碼管理功能是如何實現的,只是它根據原始程式碼管理外掛程式 API 完成。

- 實現原始程式碼管理外掛程式比原始程式碼管理 VSPackage 更容易。

## <a name="source-control-vspackage"></a>原始碼管理 VS 套件
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]允許深度整合到 Visual Studio,全面控制原始程式碼管理功能,並完全取代 Visual Studio 提供的原始程式碼管理使用者介面。 原始碼管理 VSPackage 在 Visual Studio 註冊並提供原始程式碼管理功能。 儘管多個原始程式碼管理 VSPackages 可以在 Visual Studio 中註冊,但其中只有一個可以在任何時間處於活動狀態。 源代碼管理 VSPackage 在可視化工作室處於活動狀態時可完全控制原始程式碼管理功能和外觀。 可能在系統中註冊的所有其他原始程式碼管理 VS 包處於非活動狀態,不會顯示任何 UI。

 實現原始碼管理 VSPackage 需要"全無"策略。 原始碼管理 VSPackage 的建立者必須投入大量精力來實現許多原始碼管理介面和新的 UI 元素(對話框、功能表和工具列),以涵蓋整個原始碼管理功能。 關於詳細資訊[,請參考原始碼管理 VS 套件](../../extensibility/internals/creating-a-source-control-vspackage.md)。

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>實現原始碼管理 VS 套件的缺點

- VSPackage 必須實現多個複雜的介面才能與 Visual Studio 成功整合。

- VS包必須提供原始程式碼管理所需的所有 UI;視覺工作室將在此領域不提供任何説明。

- 原始碼管理 VSPackage 與 Visual Studio 緊密相連,無法使用獨立程式運行,因此功能不能像原始程式碼管理程式的外部版本那樣容易共用。

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>實現原始碼管理 VS 套件的優勢

- 由於 VSPackage 可以完全控制原始程式碼管理 UI 和功能,因此向使用者提供了用於原始程式碼控制的無縫介面。

- VSPackage 並不局限於特定的原始程式碼管理模型。

## <a name="see-also"></a>另請參閱
- [原始碼管理](../../extensibility/internals/source-control.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [原始檔控制的新功能](../../extensibility/internals/what-s-new-in-source-control.md)
