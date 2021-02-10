---
title: 指定 ClickOnce 應用程式的 [開始] 功能表名稱
description: 瞭解如何藉由在 [發行選項] 對話方塊中設定產品名稱，來變更 ClickOnce 應用程式的顯示名稱。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9c9dee27ae78375dcb667bba5157ea84c046073
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940432"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>How to: Specify a Start menu name for a ClickOnce application (如何：指定 ClickOnce 應用程式的 [開始] 功能表名稱)
當 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式安裝在線上和離線時，[ **開始** ] 功能表和 [ **新增或移除程式** ] 清單中會加入一個專案。 根據預設，顯示名稱與應用程式元件的名稱相同，但您可以在 [**發行選項**] 對話方塊中設定 **產品名稱** 來變更顯示名稱。

 **產品名稱** 將會顯示在 *publish.htm* 頁面;若為已安裝的離線應用程式，它將會是 [ **開始** ] 功能表中的專案名稱，也會是 [ **新增或移除程式**] 中顯示的名稱。

 **發行者名稱** 將會出現在 [**產品名稱**] 的 [ *publish.htm* ] 頁面上，而針對已安裝的離線應用程式，也會是在 [**開始**] 功能表中包含應用程式圖示的資料夾名稱。

 [開始] 功能表的快捷方式或應用程式參考會以 *%Appdata%\Microsoft\Windows\Start Menu\Programs \\<發行者 \> 名稱* 來建立。 快捷方式或應用程式參考與產品名稱具有相同的名稱。

 您可以在 [**發行選項**] 對話方塊（位於 [**專案設計** 工具] 的 [**發行**] 頁面）中，設定 [**產品名稱**] 和 [**發行者名稱**] 屬性。

### <a name="to-specify-a-start-menu-name"></a>若要指定 [開始] 功能表名稱

1. 在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。

2. 按一下 [Publish (發行)]  索引標籤。

3. 按一下 [ **選項** ] 按鈕，開啟 [ **發行選項** ] 對話方塊。

4. 按一下 [ **描述**]。

5. 在 [ **發行選項** ] 對話方塊中，輸入要顯示在 **產品名稱** 中的名稱。

6. （選擇性）您可以在 **[發行者名稱]** 中輸入發行者名稱。

## <a name="see-also"></a>另請參閱
- [發佈 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)
- [如何：使用發佈精靈發佈 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)