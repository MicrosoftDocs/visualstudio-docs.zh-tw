---
title: "如何： 指定 ClickOnce 應用程式的 [開始] 功能表名稱 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: b27cf6d67cef1098a54277d4857b75d3fba0ff65
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>如何：指定 ClickOnce 應用程式的開始功能表名稱
當[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]供線上及離線使用，安裝應用程式，加入一個項目是**啟動**功能表和**新增或移除程式**清單。 根據預設，顯示名稱是應用程式組件的名稱相同，但是您可以變更顯示名稱，藉由設定**產品名稱**中**發行選項** 對話方塊。  
  
 **產品名稱**將顯示的 publish.htm 網頁; 上安裝的離線應用程式，它會是中的項目名稱**啟動**功能表上，而且也會在顯示的名稱**新增或移除程式**。  
  
 **發行者名稱**會出現在上述的 publish.htm 網頁**產品名稱**，針對已安裝的離線應用程式，它也將會是包含應用程式的圖示中的資料夾名稱**開始**功能表。  
  
 您可以設定**產品名稱**和**發行者名稱**中的屬性**發行選項**對話方塊中，用於**發行**頁面**專案設計工具**。  
  
### <a name="to-specify-a-start-menu-name"></a>若要指定的開始功能表名稱  
  
1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。  
  
2.  按一下**發行** 索引標籤。  
  
3.  按一下**選項** 按鈕以開啟**發行選項** 對話方塊。  
  
4.  按一下**描述**。  
  
5.  在**發行選項**對話方塊方塊中，輸入要在顯示的名稱**產品名稱**。  
  
6.  您可以選擇性地輸入中的發行者名稱**發行者名稱**。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)