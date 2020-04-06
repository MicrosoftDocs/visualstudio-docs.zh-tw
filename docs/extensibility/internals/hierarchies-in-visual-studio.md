---
title: 視覺工作室中的層次結構 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdbb8a0e58f6b1e5bc6e32f8c319d1480c4db4b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708194"
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio 中的階層
整合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]式開發環境 (IDE) 會顯示為*層次結構*。 在IDE中,層次結構是節點樹,其中每個節點都有一組關聯的屬性。 *專案層次結構*是一個容器,用於保存專案的項、項的關係以及項的關聯屬性和命令。

 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中,使用層次結構介面管理項目層次結構<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。 介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>將調用的命令從專案項重定向到相應的層次結構視窗,而不是標準命令處理程式。

## <a name="project-hierarchies"></a>專案層次結構
 每個專案層次結構都包含可以查看和編輯的專案。 這些專案因項目類型而異。 例如,資料庫專案可能包含存儲過程、資料庫檢視和資料庫表。 另一方面,程式設計語言專案可能包括位圖和對話方塊的源檔和資源檔。 層次結構可以嵌套,這在創建專案層次結構時為您提供了一些更大的靈活性。

 建立新項目類型時,專案類型控制可在其中編輯的完整項集。 但是,專案可以包含它們不支援的專案。 例如,Visual C++ 專案可以包含 HTML 檔,即使 Visual C++ 不為 HTML 檔案類型提供任何自訂編輯器。

 層次結構管理它們包含的項的持久性。 層次結構的實現必須控制影響層次結構中項持久性的任何特殊屬性。 例如,如果項表示存儲庫中的物件而不是檔,則層次結構實現必須控制這些物件的持久性。 IDE 本身指示層次結構按照使用者輸入保存項,但 IDE 不控制保存這些專案所需的任何操作。 相反,項目處於控制之下。

 當使用者在編輯器中打開項時,將選擇控制該項的層次結構,並成為活動層次結構。 所選層次結構確定可用於對項執行操作的命令集。 以這種方式跟蹤使用者焦點使層次結構能夠反映使用者的當前上下文。

## <a name="see-also"></a>另請參閱
- [專案類型](../../extensibility/internals/project-types.md)
- [IDE 選擇與貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
