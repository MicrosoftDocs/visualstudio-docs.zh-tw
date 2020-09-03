---
title: 疑難排解說明檢視器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: troubleshooting
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2cedc9f45d2e21684496bd882de4aa74b3bf8b3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851072"
---
# <a name="troubleshooting-the-help-viewer"></a>說明檢視器疑難排解
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題討論使用 Help Viewer 時可能會遇到的問題。

## <a name="audio-doesnt-work"></a>音訊無法運作。
 Help Viewer 未隨附音訊播放器。 如果您下載包含音訊的內容，但在選擇 [播放]**** 時卻什麼都沒發生，請安裝音訊播放器。

## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>搜尋在 Windows Server 2008、Windows Server 2008 SP1 或 Windows Server 2008 R2 中無法運作。
 Help Viewer 中的搜尋和篩選功能需要安裝並開啟 Windows Search 服務。 在 Windows Server 2008、Windows Server 2008 Service Pack 1 (SP1) 和 Windows Server 2008 R2 中，預設會關閉這項服務。

#### <a name="to-activate-windows-search-service"></a>啟動 Windows Search 服務

1. 啟動伺服器管理員。

2. 在左瀏覽窗格中，選擇 [角色]****。

3. 在 [角色摘要] 窗格中，選擇 [新增角色]****。

4. 選擇「檔案服務」角色，然後選擇 [下一步]**** 按鈕。

5. 選擇「Windows Search」角色服務。

## <a name="additional-resources"></a>其他資源
 您可以利用下列資源來取得詳細資訊，並提供 Help Viewer 的相關意見反應：

- 若要提供意見反應，請參閱 Microsoft 網站上的 [Microsoft Connect](https://connect.microsoft.com/)，或傳送電子郵件至 [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com)。

- 如需詳細資訊，請參閱 [開發人員檔，以及協助系統](https://social.msdn.microsoft.com/Forums/en-US/devdocs/threads) 論壇和 [協助專家的](https://blogs.msdn.com/b/thehelpguy/) blog。

## <a name="see-also"></a>另請參閱
 [Help Viewer 2.1 Administrator Guide](https://msdn.microsoft.com/library/hh492077(VS.110).aspx) (說明檢視器 2.1 系統管理員指南)
