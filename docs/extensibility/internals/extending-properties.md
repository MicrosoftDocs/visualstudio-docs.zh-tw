---
title: 擴展屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7064128c54434b0a7bb8799e62b751e765511c48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708423"
---
# <a name="extend-properties"></a>延伸屬性
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**屬性**視窗是 COM 和 COM+ 元件的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]通用屬性瀏覽器, 支援所有產品。 **屬性**視窗`ITypeInfo`使用 類型資訊和 COM+ 中繼資料來列出整合式開發環境 (IDE) 中任何其他視窗中當前選定的物件的設計時屬性。

 屬性**視窗**可透過按鍵盤上的**F4**或 **「檢視」** 選單上的 **「屬性視窗**」 開啟,用於查看和編輯與設定無關的設計時間屬性和選定物件的事件。 與設定相關的屬性(與解決方案與專案關聯)顯示在[屬性頁上](../../extensibility/internals/property-pages.md)。 有關詳細資訊,[管理設定選項](../../extensibility/internals/managing-configuration-options.md)。

 ![屬性視窗概述](../../extensibility/internals/media/vspropertieswindow.png "vs屬性視窗")屬性視窗

 本節提供的詳細資訊,這些資訊與**屬性**視窗的各個區域以及要填充視窗而必須實現和調用的介面有關。

## <a name="in-this-section"></a>本節內容
- [屬性視窗概述](../../extensibility/internals/properties-window-overview.md)

 解釋「**屬性」** 視窗相對於工具視窗和文件視窗的用途。

- [樣本原則與屬性視窗](../../extensibility/internals/template-policy-and-the-properties-window.md)

 討論專案如何包含在企業範本專案中,以及企業範本專案如何強制實施策略。

- [屬性視窗欄位與介面](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 解釋確定 **「屬性」** 視窗中顯示的資訊的選擇基礎。

- [屬性視窗物件清單](../../extensibility/internals/properties-window-object-list.md)

 描述**屬性**視窗物件清單的用途,描述當來自此清單的不同物件觸發調用時,如何通知環境已選擇新物件。

- [屬性視窗按鈕](../../extensibility/internals/properties-window-buttons.md)

 解釋 **「屬性」** 視窗工具列上顯示的四個預設按鈕的用途。

- [屬性顯示格線](../../extensibility/internals/properties-display-grid.md)

 說明在網格中找到屬性名稱和屬性值欄位的位置。

## <a name="related-sections"></a>相關章節
- [專案類型](../../extensibility/internals/project-types.md)

 將項目作為IDE的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]構建基塊進行討論。

- [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)

 描述如何在構建應用程式時使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]該平台進行持續測試和調試應用程式。

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 描述首先`IDispatch`用於支援自動化的介面,它提供了一個後期綁定機制來訪問和檢索有關物件的方法和屬性的資訊。

- [管理應用程式設定 (.NET)](../../ide/managing-application-settings-dotnet.md)

 提供應用程式設定的概述,這些設置允許您設定應用程式,以便屬性值存儲在外部配置檔中,而不是應用程式的編譯代碼中。

- [方案和專案](../../ide/solutions-and-projects-in-visual-studio.md)

 說明如何透過[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]解決方案和專案有效地管理專案,如引用、資料連接、資料夾和檔。

- [擴展視覺工作室的其他部分](../../extensibility/extending-other-parts-of-visual-studio.md)

 說明如何使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 服務建立 UI 項目，比對其餘的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。
