---
title: 專案上下文 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51e411f0bca361f96cdffcfd89498908fd21d441
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706591"
---
# <a name="project-context"></a>專案內容
當使用者添加或使用專案和專案項時,IDE 將使用專案上下文的概念來確定如何執行各種操作。

 通常,檔案是使用者通過選擇 **「新專案」** 命令或通過在 **「檔**」功能表上選擇 **「打開專案」** 指令而顯式創建的標準項目物件。 在這些情況下,在專案的上下文中創建和打開檔,專案類型定義用於編輯文檔的上下文。

 有些專案提供了非常豐富的上下文。 例如,專案管理用於數據綁定的專案範圍、程式設計命名空間或專案範圍資料庫連接。 用戶經常使用特定的專案物件(如解決方案資源管理員中顯示的專案項)直接打開檔案或資料庫連接。

 在其他情況下,未顯式指定項的專案上下文。 例如,當使用者透過在 **「檔」** 選單上選擇 **「打開現有檔」** 指令、除錯器對檔案進行操作或在 **「尋找」與取代**對話框中按一下「**尋找檔案」** 指令來開啟檔時,項的上下文不可用。 為了處理這些情況,IDE 調<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>用 以管理查找打開文檔的最佳項目的過程。

## <a name="see-also"></a>另請參閱
- [專案優先順序](../../extensibility/internals/project-priority.md)
- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
