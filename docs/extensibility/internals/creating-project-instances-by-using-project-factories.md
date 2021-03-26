---
title: 使用專案工廠建立專案實例 |Microsoft Docs
description: 瞭解如何使用 Visual Studio 整合式開發環境 (IDE) 中的專案 factory 來建立專案類別實例。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40b7c3fbe5b5b7fd59fe0e57376290181f3e9a20
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056791"
---
# <a name="create-project-instances-by-using-project-factories"></a>使用 project factory 建立專案實例
中的專案類型 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用 *專案 factory* 來建立專案物件的實例。 專案 factory 類似于 cocreatable COM 物件的標準 class factory。 但是，不會 cocreatable 專案物件;您只能使用專案 factory 來建立它們。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]當使用者在中載入現有的專案或建立新的專案時，IDE 會呼叫在 VSPackage 中實作為的專案 factory [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 新的專案物件提供 IDE 足夠的資訊來填入 **方案總管**。 新的專案物件也提供必要的介面，以支援 IDE 所起始的所有相關 UI 動作。

 您可以在專案的類別中執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 介面。 一般而言，它位於自己的模組中。

 支援由擁有者匯總的專案必須在其專案檔中保存擁有者金鑰。 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> 具有擁有者金鑰的專案上呼叫方法時，所擁有的專案會將其擁有者金鑰轉換為專案 FACTORY GUID，然後 `CreateProject` 在此專案 factory 上呼叫方法來進行實際建立。

## <a name="create-an-owned-project"></a>建立擁有的專案
 擁有者會以兩個階段建立所擁有的專案：

1. 藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> 方法。 這可讓擁有的專案有機會根據輸入控制來建立匯總的專案物件 `IUnknown` 。 擁有的專案會將內部 `IUnknown` 和匯總的物件傳遞回擁有者專案。 這可讓擁有的專案有機會儲存內部 `IUnknown` 。

2. 藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> 方法。 當呼叫這個方法時，擁有的專案會執行它的所有具現化，而不是呼叫，就像 `IVsProjectFactory::CreateProject` 是未擁有之專案的情況一樣。 輸入 `VSOWNEDPROJECTOBJECT` 列舉通常是匯總擁有的專案。 擁有的專案可以使用這個變數來判斷其專案物件是否已建立 (cookie 不等於 Null) 或必須建立 (cookie 等於 Null) 。

   專案類型是由唯一的專案 GUID 所識別，類似于 cocreatable COM 物件的 CLSID。 一般來說，一個專案處理站會處理建立單一專案類型的實例，雖然可以有一個專案處理站處理一個以上的專案類型 GUID。

   專案類型會與特定的副檔名相關聯。 當使用者嘗試開啟現有的專案檔，或嘗試透過複製範本來建立新的專案時，IDE 會使用該檔案上的副檔名來判斷對應的專案 GUID。

   當 IDE 判斷它是否必須建立新的專案或開啟特定類型的現有專案時，IDE 會使用 **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]** 下系統登錄中的資訊，來找出哪些 VSPackage 會執行必要的專案 factory。 IDE 會載入此 VSPackage。 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 方法中，VSPackage 必須藉由呼叫方法，在 IDE 中註冊其 project factory <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> 。

   介面的主要方法 `IVsProjectFactory` 是 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> ，這應該會處理兩種案例：開啟現有的專案並建立新專案。 大部分的專案會將其專案狀態儲存在專案檔中。 通常會建立新的專案，方法是複製一份傳遞給方法的範本檔案 `CreateProject` ，然後開啟複製。 現有的專案會藉由直接開啟傳遞給方法的專案檔來具現化 `CreateProject` 。 `CreateProject`方法可以視需要向使用者顯示額外的 UI 功能。

   專案也不能使用任何檔案，而是將其專案狀態儲存在檔案系統以外的儲存機制中，例如資料庫或 Web 服務器。 在此情況下，傳遞至方法的檔案名參數 `CreateProject` 實際上不是檔案系統路徑，而是用來識別專案資料的唯一字串（URL）。 您不需要複製傳遞給的範本檔案，就可以 `CreateProject` 觸發適當的結構順序來執行。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
