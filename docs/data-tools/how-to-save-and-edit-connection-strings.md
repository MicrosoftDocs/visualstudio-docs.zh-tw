---
title: 如何：儲存和編輯連接字串
description: 瞭解如何在 Visual Studio 應用程式中儲存和編輯連接字串。 直接在應用程式設定中儲存或編輯連接字串。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 1707bbdd458ba6fc57ea3f6897af40e4cb9b4f03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866732"
---
# <a name="how-to-save-and-edit-connection-strings"></a>如何：儲存和編輯連接字串
Visual Studio 應用程式中的連接字串會儲存在應用程式佈建檔中， (也稱為應用程式設定) ，或直接在您的應用程式中進行硬式編碼。 將連接字串儲存至應用程式組態檔，可簡化應用程式維護工作。 如果需要變更連接字串，您可以在應用程式設定檔中更新它 (而不需要在原始程式碼中變更它並重新編譯應用程式)。

在連接字串內儲存敏感性資訊 (如密碼) 會影響應用程式的安全性。 不會加密或模糊化儲存至應用程式組態檔的連接字串，因此，可能會有人存取該檔案並檢視其內容。 使用 Windows 整合式安全性是控制資料庫存取的更安全方式。

如果您未選擇使用 Windows 整合式安全性，而且您的資料庫需要使用者名稱和密碼，則可以透過連接字串省略它們，但是，您的應用程式還是需要提供此資訊才能順利連接至資料庫。 例如，您可以建立提示使用者輸入此資訊的對話方塊，並在執行階段動態建置連接字串。 如果在進出資料庫的資訊中攔截到該資訊，則安全性可能還是有問題。
如需詳細資訊，請參閱 [保護連接資訊](/dotnet/framework/data/adonet/protecting-connection-information)。

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>在資料來源設定向導內儲存連接字串
在 [ **資料來源設定]** 中，選取在 [將 **連接字串儲存到應用程式佈建檔** ] 頁面上儲存連接的選項。

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>將連接字串直接儲存至應用程式設定
1. 在 **方案總管** 中，按兩下 **我的專案** 圖示 (Visual Basic) 或 **屬性** 圖示 (C#) 來開啟 **專案設計工具**。
1. 選取 [Settings] \(設定\) 索引標籤。
1. 輸入連接字串的 **名稱**。 在程式碼中存取連接字串時，請參考此名稱。
1. 將 **類型** 設定至 (**連接字串**)。
1. 將 **領域** 設定為 **應用程式**。
1. 在 [**值**] 欄位中輸入您的連接字串，或按一下 [**值**] 欄位中的 **省略號** ( ... ) 按鈕，以開啟 [**連接屬性**] 對話方塊來建立連接字串。

## <a name="edit-connection-strings-stored-in-application-settings"></a>編輯儲存在應用程式設定中的連接字串
您可以使用 **專案設計工具** 來修改應用程式設定中所儲存的連線資訊。

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>編輯應用程式設定中儲存的連接字串
1. 在 **方案總管** 中，按兩下 **我的專案** 圖示 (Visual Basic) 或 **屬性** 圖示 (C#) 來開啟 **專案設計工具**。
1. 選取 [Settings] \(設定\) 索引標籤。
1. 找出您想要編輯的連接，然後選取 [ **值** ] 欄位中的文字。
1. 在 [**值**] 欄位中編輯連接字串，或按一下 [**值**] 欄位中的 **省略號** ( ... ) 按鈕，以使用 [**連接屬性**] 對話方塊來編輯您的連接。

## <a name="edit-connection-strings-for-datasets"></a>編輯資料集的連接字串
您可以針對資料集中的每個 TableAdapter 修改連接資訊。

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>編輯資料集中之 TableAdapter 的連接字串
1. 在 **方案總管** 中，按兩下有您要編輯之連接的資料集 (**.xsd** 檔案) 。
1. 選取具有您想要編輯之連接的 **TableAdapter** 或查詢。
1. 在 [ **屬性** ] 視窗中，展開 [ **連接] 節點**。
1. 若要快速修改連接字串，請編輯 **ConnectionString** 屬性，或按一下 **連接** 屬性上的向下箭號，然後選擇 [ **新增連接**]。

## <a name="security"></a>安全性
在連接字串內儲存敏感性資訊 (如密碼) 會影響應用程式的安全性。 使用 Windows 整合式安全性是控制資料庫存取的更安全方式。
如需詳細資訊，請參閱 [保護連接資訊](/dotnet/framework/data/adonet/protecting-connection-information)。

## <a name="see-also"></a>另請參閱

- [新增連接](../data-tools/add-new-connections.md)
