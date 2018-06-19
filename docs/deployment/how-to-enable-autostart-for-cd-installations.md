---
title: 如何： 啟用 CD 安裝的 AutoStart |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 230f0491993b3804c3147e727900de2647ff7bda
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558239"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>如何：啟用 CD 安裝的 AutoStart
部署時[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]透過卸除式媒體例如 CD-ROM 或 DVD-ROM 應用程式，您可以啟用`AutoStart`以便[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]插入媒體時，自動啟動應用程式。  
  
 `AutoStart` 可在啟用**發行**頁面**專案設計工具**。  
  
### <a name="to-enable-autostart"></a>若要啟用自動啟動  
  
1.  選取方案總管 中的專案，然後按一下 [專案]  功能表中的 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**選項** 按鈕。  
  
     **發行選項** 對話方塊隨即出現。  
  
4.  按一下**部署**。  
  
5.  選取**若是使用光碟安裝，安裝程式啟動時自動啟動 CD 插入**核取方塊。  
  
     Autorun.inf 檔案會複製到發行位置，在發行應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)