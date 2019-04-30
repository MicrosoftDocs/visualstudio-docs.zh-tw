---
title: HOW TO：儲存和編輯連接字串
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1f8300043f9a16c7d92d72c4dcb22e4cd0432a06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566967"
---
# <a name="how-to-save-and-edit-connection-strings"></a>HOW TO：儲存和編輯連接字串
在 Visual Studio 應用程式中的連接字串儲存在應用程式組態檔 （也稱為應用程式設定），或硬式編碼直接在您的應用程式中。 將連接字串儲存至應用程式組態檔，可簡化應用程式維護工作。 如果需要變更連接字串，您可以在應用程式設定檔中更新它 (而不需要在原始程式碼中變更它並重新編譯應用程式)。

在連接字串內儲存敏感性資訊 (如密碼) 會影響應用程式的安全性。 不會加密或模糊化儲存至應用程式組態檔的連接字串，因此，可能會有人存取該檔案並檢視其內容。 使用 Windows 整合式安全性是控制資料庫存取的更安全方式。

如果您未選擇使用 Windows 整合式安全性，而且您的資料庫需要使用者名稱和密碼，則可以透過連接字串省略它們，但是，您的應用程式還是需要提供此資訊才能順利連接至資料庫。 例如，您可以建立提示使用者輸入此資訊的對話方塊，並在執行階段動態建置連接字串。 如果在進出資料庫的資訊中攔截到該資訊，則安全性可能還是有問題。
如需詳細資訊，請參閱[保護連線資訊](/dotnet/framework/data/adonet/protecting-connection-information)。

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>若要儲存的資料來源組態精靈 中的連接字串
在 **資料來源組態精靈**，選取選項來將連接儲存在**將連接字串儲存到應用程式組態檔**頁面。

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>將連接字串直接儲存至應用程式設定
1. 在**方案總管** 中，按兩下**我的專案**圖示 (Visual Basic) 或**屬性**圖示 (C#) 來開啟**專案設計工具**。
1. 選取 [設定] 索引標籤。
1. 輸入連接字串的**名稱**。 在程式碼中存取連接字串時，請參考此名稱。
1. 將**類型**設定至 (**連接字串**)。
1. 將**領域**設定為**應用程式**。
1. 輸入您的連接字串**值**欄位中，或按一下**省略符號**中的 [（...）] 按鈕**值**欄位，以開啟**連接屬性**對話方塊，即可建置連接字串。

## <a name="edit-connection-strings-stored-in-application-settings"></a>編輯連接字串儲存在應用程式設定
您可以使用**專案設計工具**來修改應用程式設定中所儲存的連線資訊。

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>編輯應用程式設定中儲存的連接字串
1. 在**方案總管** 中，按兩下**我的專案**圖示 (Visual Basic) 或**屬性**圖示 (C#) 來開啟**專案設計工具**。
1. 選取 [設定] 索引標籤。
1. 找出您想要編輯選取的文字中的連線**值**欄位。
1. 編輯中的連接字串**值**欄位，或按一下 [**省略符號**中的 [（...）] 按鈕**值**欄位，編輯您的連線與**連線屬性**] 對話方塊。

## <a name="edit-connection-strings-for-datasets"></a>編輯資料集的連接字串
您可以修改資料集內的每個 TableAdapter 的連接資訊。

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>若要編輯的連接字串中的資料集的 TableAdapter
1. 在 **方案總管 中**，連按兩下 資料集 (**.xsd**檔案) 具有您想要編輯的連接。
1. 選取  **TableAdapter**或查詢具有您想要編輯的連接。
1. 在 [**屬性**] 視窗中，展開**連線節點**。
1. 若要快速修改連接字串，請編輯**ConnectionString**屬性，或按一下向下箭號**連線**屬性，然後選擇 **新連線**。

## <a name="security"></a>安全性
在連接字串內儲存敏感性資訊 (如密碼) 會影響應用程式的安全性。 使用 Windows 整合式安全性是控制資料庫存取的更安全方式。
如需詳細資訊，請參閱[保護連線資訊](/dotnet/framework/data/adonet/protecting-connection-information)。

## <a name="see-also"></a>另請參閱

- [新增連線](../data-tools/add-new-connections.md)