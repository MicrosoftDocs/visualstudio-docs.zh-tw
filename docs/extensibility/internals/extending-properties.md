---
title: 擴充屬性 |Microsoft Docs
description: 瞭解您必須執行的介面，以及在 Visual Studio 屬性視窗中擴充屬性清單的呼叫。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9a777bf11f388873978f450184f1455236e9ff9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887077"
---
# <a name="extend-properties"></a>擴充屬性
[ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **屬性** ] 視窗是適用于 COM 和 com + 元件的通用屬性瀏覽器，並支援所有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 產品。 [ **屬性** ] 視窗適用于 `ITypeInfo` 型別資訊和 com + 中繼資料，可在整合式開發環境 (IDE) 的任何其他視窗中，列出目前所選物件的設計階段屬性。

 [**屬性**] 視窗（可透過在鍵盤上按 **F4** 來開啟，或在 [**視圖**] 功能表上選取 [**屬性] 視窗**）是用來查看和編輯所選物件的與設定無關的設計階段屬性和事件。 與解決方案和專案相關聯的設定相依屬性會顯示在 [屬性頁](../../extensibility/internals/property-pages.md)上。 如需詳細資訊，請 [管理設定選項](../../extensibility/internals/managing-configuration-options.md)。

 ![屬性視窗總覽](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") 屬性視窗

 本節提供的詳細資訊與 [ **屬性** ] 視窗的個別區域，以及您必須執行並呼叫以填入視窗的介面相關。

## <a name="in-this-section"></a>本節內容
- [屬性視窗總覽](../../extensibility/internals/properties-window-overview.md)

 說明 [ **屬性** ] 視窗相對於工具視窗和文件視窗的用途。

- [範本原則和屬性視窗](../../extensibility/internals/template-policy-and-the-properties-window.md)

 討論如何將專案包含在企業範本專案中，以及該企業範本專案如何強制執行原則。

- [屬性視窗欄位和介面](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 說明選取專案的基礎，以決定要在 [ **屬性** ] 視窗中顯示哪些資訊。

- [屬性視窗物件清單](../../extensibility/internals/properties-window-object-list.md)

 描述 [ **屬性** ] 視窗物件清單的用途，描述如何，當這份清單中的不同物件觸發呼叫時，會通知環境已選取新的物件。

- [屬性視窗按鈕](../../extensibility/internals/properties-window-buttons.md)

 說明 [ **屬性** ] 視窗工具列上顯示的四個預設按鈕的用途。

- [屬性顯示格線](../../extensibility/internals/properties-display-grid.md)

 說明在方格中找到屬性名稱和屬性值欄位的位置。

## <a name="related-sections"></a>相關章節
- [專案類型](../../extensibility/internals/project-types.md)

 討論專案作為 IDE 的組建區塊 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)

 描述 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 當您建立應用程式時，如何使用此平臺來持續測試和偵測應用程式。

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 描述 `IDispatch` 第一次設計來支援自動化的介面，提供晚期繫結機制來存取和取得物件之方法和屬性的相關資訊。

- [管理應用程式設定 (.NET)](../../ide/managing-application-settings-dotnet.md)

 提供應用程式設定的總覽，讓您設定應用程式，讓屬性值儲存在外部設定檔中，而不是應用程式的已編譯器代碼。

- [方案和專案](../../ide/solutions-and-projects-in-visual-studio.md)

 說明如何 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 有效率地管理透過方案和專案開發工作所需的專案，例如參考、資料連線、資料夾和檔案。

- [延伸 Visual Studio 的其他部分](../../extensibility/extending-other-parts-of-visual-studio.md)

 說明如何使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 服務建立 UI 項目，比對其餘的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。
