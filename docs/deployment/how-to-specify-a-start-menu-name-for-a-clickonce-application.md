---
title: 如何： 指定 ClickOnce 應用程式的開始功能表名稱 |Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ab55674cd1de54881eb46b47997a943678cbacd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635614"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>How to: Specify a Start menu name for a ClickOnce application (如何：指定 ClickOnce 應用程式的 [開始] 功能表名稱)
當[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式已安裝的線上和離線使用，一個項目加入至**開始**功能表和**新增或移除程式**清單。 根據預設，顯示名稱是應用程式組件的名稱相同，但您可以設定來變更顯示名稱**產品名稱**中**發行選項** 對話方塊。

 **產品名稱**將會顯示在*publish.htm*頁面上，安裝的離線應用程式，就會是名稱中的項目**啟動** 功能表中，而且也會在顯示的名稱**新增或移除程式**。

 **發行者名稱**會出現在*publish.htm*頁面上方**產品名稱**，並已安裝的離線應用程式，也會包含應用程式的資料夾名稱中的圖示**啟動**功能表。

 在建立開始功能表捷徑或應用程式參考 *%appdata%\Microsoft\Windows\Start Menu\Programs\\< 發行者名稱\>*。 快顯或應用程式參考具有相同的名稱，為產品名稱。

 您可以設定**產品名稱**並**發行者名稱**中的屬性**發行選項**對話方塊中，位於**發行**頁面**專案設計工具**。

### <a name="to-specify-a-start-menu-name"></a>若要指定的開始功能表名稱

1.  在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2.  按一下 [發佈] 索引標籤。

3.  按一下 **選項** 按鈕以開啟**發行選項** 對話方塊。

4.  按一下 **描述**。

5.  在 **發行選項**對話方塊方塊中，輸入要在顯示的名稱**產品名稱**。

6.  （選擇性） 您可以在其中輸入中的 「 發行者 」 名稱**發行者名稱**。

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)