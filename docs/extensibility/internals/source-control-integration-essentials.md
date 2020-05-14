---
title: 源代碼管理集成要點 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e56658d644720f1563d71d3d08bf35268119112f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705243"
---
# <a name="source-control-integration-essentials"></a>原始檔控制整合的基本資訊
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援兩種類型的原始程式碼管理整合:一種是原始程式碼管理外掛程式,提供基本功能,並使用原始程式碼管理外掛程式 API(以前稱為 MSSCCI API)構建,另一種基於 VSPackage 的源代碼管理整合解決方案提供更強大的功能。

## <a name="source-control-plug-in"></a>原始程式管理外掛程式
 原始程式碼管理外掛程式編寫為 DLL,用於實現原始碼管理外掛程式 API。 註冊和原始程式碼管理整合功能透過 API 提供。 此方法比原始程式碼管理 VSPackage 更容易實現,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]並且它使用使用者介面 (UI) 執行大多數原始程式碼管理操作。

 要使用原始碼管理外掛程式 API 實作原始程式,請按照以下步驟操作:

1. 建立實現[原始程式碼管理外掛程式](../../extensibility/source-control-plug-ins.md)中指定的函數的 DLL。

2. 通過創建適當的註冊表項註冊 DLL,如[「如何:安裝原始程式碼管理外掛程式](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)」中所述。

3. 創建幫助程式 UI 並在原始碼管理卡接器套件(透過原始碼管理外掛程式[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]處理原始碼管理功能的元件)提示時顯示它。

   關於詳細資訊,請參考[原始碼管理外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)。

## <a name="source-control-vspackage"></a>原始碼管理 VS 套件
 原始碼管理 VSPackage 實現允許[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]您為原始碼管理 UI 開發自訂取代。 此方法提供對原始程式碼管理整合的完全控制,但它要求您提供 UI 元素並實現在外掛程式方法下提供的原始程式碼管理介面。

 要實現原始碼管理 VSPackage,您必須:

1. 建立並註冊您自己的原始程式碼管理 VSPackage,如[註冊和選擇](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)中所述。

2. 將預設原始碼管理 UI 替換為自訂 UI。 請參考[自訂使用者介面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)。

3. 指定要使用的字形,並處理**解決方案資源管理器**字形事件。 請參考[字形控制器](../../extensibility/internals/glyph-control-source-control-vspackage.md)。

4. 處理查詢編輯和查詢保存事件,如[查詢編輯查詢儲存 中](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)所示。

   關於詳細資訊,請參考[原始碼管理 VS 套件](../../extensibility/internals/creating-a-source-control-vspackage.md)。

## <a name="see-also"></a>另請參閱
- [概觀](../../extensibility/internals/source-control-integration-overview.md)
- [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [建立原始檔控制 VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)
