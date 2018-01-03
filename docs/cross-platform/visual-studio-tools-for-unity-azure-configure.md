---
title: "Visual Studio Tools for Unity Azure 逐步解說設定 | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: BAE62C27-CA7A-4466-8738-3DB880221CE1
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 25424ea06c01224bb1b35f783be82a857b991adf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="configure-easy-tables-in-azure"></a>在 Azure 中設定簡易表

簡易表是 [Azure 行動應用程式](https://azure.microsoft.com/services/app-service/mobile/)的一項功能，允許直接在 Azure 入口網站 GUI 中設定及管理的 SQL 資料表。 Azure 行動應用程式支援許多功能，但此範例的討論範圍僅限於從 Unity 專案讀取儲存在 Azure 行動應用程式後端的資料，以及將資料寫入其中。

## <a name="create-a-new-azure-mobile-app"></a>建立新的 Azure 行動應用程式

登入 [Azure 入口網站](https://ms.portal.azure.com)。 如果您沒有 Azure 訂用帳戶，[免費試用版](https://azure.microsoft.com/en-us/free/)或 [Visual Studio Dev Essentials](https://www.visualstudio.com/dev-essentials/) 中所包含的信用額度將足以完成本逐步解說。

**在入口網站中：**

1. 選取 [新增] > [Web + 行動] > [行動應用程式] > [建立]。

  ![建立新的行動應用程式](media/vstu_azure-configure-easy-tables-image1.png)

2. 設定新的行動應用程式：

  * **應用程式名稱**。 這會建立用來連線到 Azure 行動應用程式後端的 URL。 您必須選擇唯一的名稱 (以綠色核取記號表示)。

  * **訂用帳戶**。 選擇新的行動應用程式將用於計費的訂用帳戶。

  * **資源群組**。 資源群組可讓您更輕鬆地管理相關的資源。 根據預設，Azure 會使用與新應用程式相同的名稱來建立新的資源群組。 此預設設定對本逐步解說便已足夠。

  *  **App Service 方案/位置**。 服務方案指定 Azure 用來裝載新行動應用程式的運算能力、位置和資源成本。 根據預設，Azure 會使用一些預設設定來建立新的服務方案。 這是本逐步解說最簡單的選項。 不過，您可以使用此功能表來自訂新服務方案的定價層或地理位置。 此外，您可以在部署服務方案之後修改其設定。

  ![建立新的行動應用程式](media/vstu_azure-configure-easy-tables-image2.png)

3. 選取 [建立]，讓 Azure 花幾分鐘的時間來部署新的資源。 完成部署之後，您會在 Azure 入口網站中看到一則通知。

## <a name="add-a-new-data-connection"></a>新增資料連線

4. 完成部署之後，按一下 [所有資源] 按鈕，然後選取新建立的行動應用程式。

  ![選取新的行動應用程式](media/vstu_azure-configure-easy-tables-image3.png)

5. 在新開啟的刀鋒視窗中，向下捲動左邊功能表，按一下列於 [行動] 標題下的 [簡易表] 按鈕。

  ![選取 [簡易表]](media/vstu_azure-configure-easy-tables-image4.png)

6. 按一下沿著 [簡易表] 刀鋒視窗頂端顯示的藍色 [需要設定簡易表/簡易 API] 通知。

  ![按一下設定簡易表通知](media/vstu_azure-configure-easy-tables-image5.png)

7. 按一下指出 [您需要資料庫才能使用簡易表。按一下這裡建立一個。] 的通知。

  ![按一下建立資料庫通知](media/vstu_azure-configure-easy-tables-image6.png)

8. 在 [資料連線] 刀鋒視窗中，按一下 [新增] 按鈕。

  ![按一下 [新增] 按鈕](media/vstu_azure-configure-easy-tables-image7.png)

9. 在 [新增資料連線] 刀鋒視窗中，選取 [SQL 資料庫]。

  ![選取 [SQL 資料庫]](media/vstu_azure-configure-easy-tables-image8.png)

10. 這會開啟刀鋒視窗，以便設定新的 SQL 資料庫和 SQL Server：

  * **名稱**。 輸入資料庫的名稱。

  * **目標伺服器**。 按一下 [目標伺服器] 開啟 [新伺服器] 刀鋒視窗。

      * **伺服器名稱**。 輸入伺服器的名稱。

      * **伺服器管理員登入和密碼**。 建立伺服器管理員的使用者名稱和密碼。

      * **位置**。 選擇伺服器的鄰近位置。

      * 確定 [允許 AZURE 服務存取伺服器] 核取方塊保持核取狀態。

      * 按一下 [選取] 完成設定伺服器。

    * **定價層**。 針對本逐步解說保留預設設定。 稍後可進行修改。

    * **定序**。 保留預設設定。

    * 按一下 [選取] 完成設定資料庫。

    ![設定 SQL Server 和資料庫](media/vstu_azure-configure-easy-tables-image9.png)

11. 回到 [新增資料連線] 刀鋒視窗，按一下 [連接字串]。 當 [連接字串] 刀鋒視窗出現時，保留預設設定並按一下 [確定]。

  ![按一下 [連接字串]](media/vstu_azure-configure-easy-tables-image9.1.png)

12. 回到 [新增資料連線] 刀鋒視窗，"MS_TableConnectionString" 文字應該不再是斜體。 按一下 [確定]，讓 Azure 花幾分鐘的時間來建立新的資料連線。 完成程序時會收到通知。

  ![按一下 [確定]](media/vstu_azure-configure-easy-tables-image9.2.png)

## <a name="complete-the-easy-table-initialization"></a>完成簡易表初始化

13. 成功建立新的資料連線之後，按一下 [所有資源] 按鈕，再次巡覽回到行動應用程式。 您必須完成此步驟，才能重新整理簡易表設定通知。

14. 向下捲動並選取 [簡易表]，然後再次選取藍色的 [需要設定簡易表/簡易 API] 通知。

  ![按一下簡易表通知](media/vstu_azure-configure-easy-tables-image5.png)

15. 此時會顯示刀鋒視窗，在 **1** 標題下指出「您已有資料連線」。 在 **2** 標題下，按一下指出 [我了解此將覆寫所有網站內容] 的核取方塊。 現在按一下 [將應用程式初始化]，並等候幾分鐘讓 Azure 完成初始化程序。 完成程序時會宣佈新的通知。

  ![按一下 [將應用程式初始化]](media/vstu_azure-configure-easy-tables-image10.png)

## <a name="next-step"></a>後續步驟

* [建立簡易表](visual-studio-tools-for-unity-azure-setup.md)
