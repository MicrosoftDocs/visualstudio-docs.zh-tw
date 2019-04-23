---
title: HOW TO：指定 ClickOnce 應用程式的開始功能表名稱 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 30bb4050399bf7a6d9120f7e5454b26ce505af35
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061550"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>HOW TO：指定 ClickOnce 應用程式的開始功能表名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式已安裝的線上和離線使用，一個項目加入至**開始**功能表和**新增或移除程式**清單。 根據預設，顯示名稱是應用程式組件的名稱相同，但您可以設定來變更顯示名稱**產品名稱**中**發行選項** 對話方塊。  
  
 **產品名稱**將顯示的 publish.htm 網頁; 上已安裝的離線應用程式，它會是名稱中的項目**開始**功能表上，而且也會在顯示的名稱**新增或移除程式**。  
  
 **發行者名稱**會出現在上述的 publish.htm 網頁**Product name**，並已安裝的離線應用程式，也會包含應用程式的圖示中的資料夾名稱**開始**功能表。  
  
 您可以設定**產品名稱**並**發行者名稱**中的屬性**發行選項**對話方塊中，位於**發行**頁面**專案設計工具**。  
  
### <a name="to-specify-a-start-menu-name"></a>若要指定的開始功能表名稱  
  
1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2. 按一下 [發佈] 索引標籤。  
  
3. 按一下 **選項** 按鈕以開啟**發行選項** 對話方塊。  
  
4. 按一下 **描述**。  
  
5. 在 **發行選項**對話方塊方塊中，輸入要在顯示的名稱**產品名稱**。  
  
6. （選擇性） 您可以在其中輸入中的 「 發行者 」 名稱**發行者名稱**。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用 [發佈精靈] 發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
