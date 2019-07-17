---
title: 作法：啟用 CD 安裝的 AutoStart |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4bd14060517793d28e24818a051df63efb8f0e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153790"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>作法：啟用 CD 安裝的 AutoStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

部署時[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]透過卸除式媒體例如 CD-ROM 或 DVD-ROM 的應用程式，您可以讓`AutoStart`以便[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]插入媒體時，將會自動啟動應用程式。  
  
 `AutoStart` 您可以上啟用**發佈**頁面**專案設計工具**。  
  
### <a name="to-enable-autostart"></a>若要啟用自動啟動  
  
1. 選取方案總管  中的專案，然後按一下 [專案]  功能表中的 [屬性]  。  
  
2. 按一下 [發佈]  索引標籤。  
  
3. 按一下 [選項]  按鈕。  
  
     **發行選項** 對話方塊隨即出現。  
  
4. 按一下 **部署**。  
  
5. 選取 **若是使用光碟安裝時自動啟動安裝程式插入光碟後**核取方塊。  
  
     Autorun.inf 檔案會複製到發行位置，在發行應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用 [發佈精靈] 發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
