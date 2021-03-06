---
title: 建立新專案
description: 瞭解如何在 Visual Studio 中建立新專案。
ms.custom: SEO-VS-2020
ms.date: 12/23/2020
ms.topic: how-to
f1_keywords:
- vs.newproject
helpviewer_keywords:
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05cfb7cf053a3275b49b76b46bec8054fb105078
ms.sourcegitcommit: 529e1716924c3e1ac8a750550b996ad3c79f353b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/14/2021
ms.locfileid: "112066952"
---
# <a name="create-a-new-project-in-visual-studio"></a>在 Visual Studio 中建立新專案

在本文中，我們將示範如何在 Visual Studio 範本中快速建立新專案。

::: moniker range="vs-2017"

## <a name="open-the-new-project-dialog"></a>開啟 [新增專案] 對話方塊

有多種方式可在 Visual Studio 2017 中建立新的專案。 在 [開始] 頁面上，您可以在 [ **搜尋專案範本** ] 方塊中輸入專案範本的名稱，或選取 [ **建立新專案** ] 連結來開啟 [ **新增專案** ] 對話方塊。 除了 [開始] 頁面之外，您也可以 **選取**  >    >  功能表列上的 [檔案新 **專案**]，或按一下工具列上的 [**新增專案**] 按鈕。

![Visual Studio 中的功能表列螢幕擷取畫面，其中已選取 [> 新 > 專案選項。](./media/vside-newproject1.png)

## <a name="select-a-template-type"></a>選取範本類型

在 [新增專案] 對話方塊中，可用的專案範本會出現在清單中的 [範本] 類別下。 範本會依程式設計語言和專案類型組織，例如 Visual C#、JavaScript 和 Azure Data Lake。

![[新增專案] 對話方塊的螢幕擷取畫面，其中顯示已安裝的範本清單。](./media/vside-newproject-templates-list.png)

> [!NOTE]
> 所顯示的可用語言和專案範本清單取決於您執行的 Visual Studio 版本及安裝的工作負載。 若要了解如何安裝額外的工作負載，請參閱[透過新增或移除工作負載和元件來修改 Visual Studio](../install/modify-visual-studio.md)。

按一下語言名稱旁的三角形，然後選擇專案類別 (例如 Windows Desktop)，顯示您要使用之程式設計語言的範本清單。

下圖示範適用於 Visual C# .NET Core 專案的專案範本：

![[新增專案] 對話方塊的螢幕擷取畫面，其中列出您可以選擇的專案範本。](./media/new-project-dialog-net-core.png)

## <a name="configure-your-project"></a>設定您的專案

在 [名稱] 方塊中輸入新專案的名稱。 您可以將專案儲存在電腦的預設位置，或按一下 [瀏覽] 按鈕尋找其他位置。 您也可以選取方案名稱，或選取 [ **加入至原始檔控制** ]) ，將新的專案新增至 Git 存放庫 (。

按一下 [確定] 建立解決方案和專案。

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-the-create-a-new-project-page"></a>開啟 [建立新專案] 頁面

有多種方式可在 Visual Studio 2019 中建立新的專案。 當您第一次開啟 Visual Studio 時，[開始] 視窗隨即出現，而您可以從該處選取 [ **建立新專案**]。

:::image type="content" source="media/vs-2019/start-window-create-new-project.png" alt-text="在 Visual Studio 2019 的 [開始] 視窗中，[建立新專案] 對話方塊的螢幕擷取畫面":::

如果 Visual Studio 開發環境已經開啟，您 **可以選擇**  >    >  功能表列上的 [檔案新增 **專案**] 來建立新專案。 您也可以按一下工具列上的 [**新增專案**] 按鈕，或按下 **Ctrl** + **Shift** + **N**。

:::image type="content" source="media/vs-2019/new-project-button.png" alt-text="Visual Studio 2019 中 [新增專案] 按鈕的螢幕擷取畫面。":::

## <a name="select-a-template-type"></a>選取範本類型

在 [建立新專案] 頁面上，您最近選取的範本清單會出現在左邊。 範本會依「最近使用」來排序。

如未從最近使用的範本中選取，您可依 [語言] (例如，C# 或 C++)、[平台] (例如 Windows 或 Azure) 和 [專案類型] (例如，Desktop 或 Web) 篩選所有可用的專案範本。 您也可以在 [搜尋] 方塊中輸入搜尋文字，進一步篩選範本；例如，**asp.net**。

:::image type="content" source="media/vs-2019/create-new-project-filters.png" alt-text="Visual Studio 2019 中專案範本篩選的螢幕擷取畫面。":::

出現在每個範本下的標籤會對應至三個下拉式清單篩選器 ([語言]、[平台] 和 [專案類型])。

> [!TIP]
> 如果您沒有看到您要尋找的範本，您可能缺少 Visual Studio 的工作負載。 若要安裝額外的工作負載；例如，**Azure 開發** 或 **使用 .NET 進行行動開發**，請按一下 [安裝更多工具與功能] 連結開啟 Visual Studio 安裝程式。 從該處選取您要安裝的工作負載，然後選取 [ **修改**]。 然後，就有其他的專案範本可供選擇。
>
> :::image type="content" source="media/vs-2019/install-more-tools-features.png" alt-text="Visual Studio 2019 的 [安裝更多工具和功能] 連結的螢幕擷取畫面。":::

選取範本，然後按一下 [下一步]。

## <a name="configure-your-project"></a>設定您的專案

[ **設定您的新專案** ] 頁面中有選項可將您的專案命名 (和方案) 、選取磁片位置，以及選取架構版本 (如果適用于您選擇的範本) 。

:::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Visual Studio 2019 中 [設定您的新專案] 頁面的螢幕擷取畫面。":::

> [!NOTE]
> 如在已使用 Visual Studio 開啟專案或解決方案的情況下建立新的專案，則有額外的組態選項可用。 您可以選擇建立新的解決方案，或將新專案新增至已開啟的解決方案。
>
> :::image type="content" source="media/vs-2019/configure-new-project-solution.png" alt-text="Visual Studio 2019 中 [建立新方案] 或 [新增至方案] 對話方塊的螢幕擷取畫面。":::

按一下 [建立] 建立新的專案。

::: moniker-end

## <a name="add-additional-projects-to-a-solution"></a>將其他專案新增至解決方案

如果您想要將其他專案新增至方案，請以滑鼠右鍵按一下 **方案總管** 中的方案節點，然後選取 [**加入**  >  **新專案**]。

> [!TIP]
> 如需從頭開始建立的專案和解決方案範例，請參閱 [專案和方案簡介](../get-started/tutorial-projects-solutions.md)（請參閱）。

## <a name="see-also"></a>另請參閱

- [專案和解決方案簡介](../get-started/tutorial-projects-solutions.md)
- [使用解決方案與專案](creating-solutions-and-projects.md)
- [管理專案和解決方案屬性](managing-project-and-solution-properties.md)
- [建立專案 (Visual Studio for Mac)](/visualstudio/mac/create-new-projects)
