---
title: 如何：設定 ClickOnce 發行版本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ec5d5d742b5a0749d1d5d52cee0a0545dd8570f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838929"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>如何：設定 ClickOnce 發行版本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `Publish Version` 屬性會決定您要發佈的應用程式是否會被視為更新。 每次版本都會遞增，應用程式將會發佈為更新。  
  
 您 `Publish Version` 可以在 [**專案設計**工具] 的 [**發行**] 頁面上設定屬性。  
  
> [!NOTE]
> 專案選項會在 `Publish Version` 每次發行應用程式時自動遞增屬性; 此選項預設為啟用。 如需詳細資訊，請參閱 [如何：自動遞增 ClickOnce 發行版本](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)。  
  
### <a name="to-change-the-publish-version"></a>變更發行版本  
  
1. 在 **方案總管**中選取專案時，在 [ **專案** ] 功能表上按一下 [ **屬性**]。  
  
2. 按一下 [Publish (發行)] **** 索引標籤。  
  
3. 在 [ **發行版本** ] 欄位中，遞增 **主要**、 **次要**、 **組建**或 **修訂** 版本號碼。  
  
    > [!NOTE]
    > 您永遠不應該遞減版本號碼;這樣做可能會導致無法預期的更新行為。  
  
## <a name="see-also"></a>另請參閱  
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [如何：自動遞增 ClickOnce 發行版本](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發佈嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
