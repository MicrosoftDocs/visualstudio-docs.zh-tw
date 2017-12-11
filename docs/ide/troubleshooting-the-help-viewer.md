---
redirect_url: /visualstudio/ide/microsoft-help-viewer
ms.openlocfilehash: c0b1a114eb157860dd70873929727cc56f1d6514
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
title: "針對 Help Viewer 進行疑難排解 | Microsoft Docs" ms.custom: "" ms.date: "11/04/2016" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "針對 [Help Viewer] 進行疑難排解"
  - "針對 Help Viewer 進行疑難排解" ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12 caps.latest.revision: 13 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="troubleshooting-the-help-viewer"></a>說明檢視器疑難排解
本主題討論使用 Help Viewer 時可能會遇到的問題。  
  
## <a name="audio-doesnt-work"></a>音訊無法運作。  
 Help Viewer 未隨附音訊播放器。 如果您下載包含音訊的內容，但在選擇 [播放] 時卻什麼都沒發生，請安裝音訊播放器。  
  
## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>搜尋在 Windows Server 2008、Windows Server 2008 SP1 或 Windows Server 2008 R2 中無法運作。  
 Help Viewer 中的搜尋和篩選功能需要安裝並開啟 Windows Search 服務。 在 Windows Server 2008、Windows Server 2008 Service Pack 1 (SP1) 和 Windows Server 2008 R2 中，預設會關閉這項服務。  
  
#### <a name="to-activate-windows-search-service"></a>啟動 Windows Search 服務  
  
1.  啟動伺服器管理員。  
  
2.  在左瀏覽窗格中，選擇 [角色]。  
  
3.  在 [角色摘要] 窗格中，選擇 [新增角色]。  
  
4.  選擇「檔案服務」角色，然後選擇 [下一步] 按鈕。  
  
5.  選擇「Windows Search」角色服務。  
  
## <a name="additional-resources"></a>其他資源  
 您可以利用下列資源來取得詳細資訊，並提供 Help Viewer 的相關意見反應：  
  
-   若要提供意見反應，請參閱 Microsoft 網站上的 [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983)，或傳送電子郵件至 [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com)。  
  
-   如需詳細資訊，請瀏覽[開發人員文件和說明系統](http://go.microsoft.com/fwlink/?LinkId=232741)論壇。  
  
## <a name="see-also"></a>請參閱
[說明檢視器系統管理員指南](http://go.microsoft.com/fwlink/?LinkId=243985)