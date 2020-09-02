---
title: 如何：啟用 CD 安裝的 AutoStart |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153790"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>如何：啟用 CD 安裝的 AutoStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

藉由卸載 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 式媒體（例如 cd-rom 或 dvd-rom）部署應用程式時，您可以啟用， `AutoStart` 讓 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式在插入媒體時自動啟動。  
  
 `AutoStart`可以在 [**專案設計**工具] 的 [**發行**] 頁面上啟用。  
  
### <a name="to-enable-autostart"></a>啟用自動啟動  
  
1. 在 **方案總管**中選取專案時，在 [ **專案** ] 功能表上按一下 [ **屬性**]。  
  
2. 按一下 [Publish (發行)] **** 索引標籤。  
  
3. 按一下 [ **選項** ] 按鈕。  
  
     [ **發行選項** ] 對話方塊隨即出現。  
  
4. 按一下 [部署]****。  
  
5. 選取 [若 **要安裝 cd，請在插入光碟時自動啟動安裝** ] 核取方塊。  
  
     發行應用程式時，會將自動完成 .inf 檔案複製到發行位置。  
  
## <a name="see-also"></a>另請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發佈嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
