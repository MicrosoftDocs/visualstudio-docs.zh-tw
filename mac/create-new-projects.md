---
title: 建立新的專案和方案
description: 本文描述如何在 Visual Studio for Mac 中建立專案和方案
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: 10fcb52a8e1311f3e8128361ee835f6ddcb3670d
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "75678875"
---
# <a name="create-a-new-project"></a>建立新的專案

## <a name="opening-the-project-creation-dialog"></a>開啟專案建立對話方塊

有幾種方式可在 Visual Studio for Mac 中建立新的專案。 首次打開 Mac 的視覺化工作室時，將顯示啟動視窗。 從這裡，您可以選擇 **"新建"，** 該功能將帶您到專案創建螢幕。

> [!TIP]
> 此外，從啟動視窗，您還可以打開和搜索最近的專案和解決方案。 您也可以移至功能表列並選擇 [檔案] > [最近使用的解決方案]****

![使用創建新專案啟動視窗](media/first-run-project.png)

如果 Visual Studio for Mac 已經開啟並載入解決方案，您可以移至功能表列並選擇 [檔案] > [新增解決方案]**** 來建立新的解決方案。 以這種方式創建新解決方案將關閉已載入的解決方案。

## <a name="creating-a-new-project-from-a-template"></a>從範本建立新專案

[新增專案]**** 對話方塊預設會顯示您最近使用的範本，並依「最近用過的順序」** 排序。

如果您不想要使用最近用過的範本，您可以從對話方塊左側的類別中選擇。 每個類別都包含數個專案範本供您選擇。 按一下專案類型可讓您在畫面右側查看描述。

![新增專案畫面](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>設定您的新專案

在您選擇專案範本之後，後續畫面將會引導您完成設定該專案所需的任何設定步驟；這些步驟可能會因專案類型而有所不同。

所有專案都需要新的專案，以及儲存檔案的位置。 如果該專案是新解決方案的一部分，而不是要將它加入至現有的解決方案，則也會需要提供解決方案名稱。

在此階段您也可以選擇設定 Git 原始檔控制選項。 下圖是某個 .NET Core 專案最終設定步驟的範例：

![設定新專案](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>將其他專案新增至解決方案

您可以滑鼠右鍵按一下 Solution Pad 中的解決方案，並選擇 [新增] > [加入新的專案]**** 或 [新增] > [加入現有專案]**** 來加入其他專案。

加入新專案將會引導您完成專案建立程序，如[設定您的新專案](#configuring-your-new-project)中所示。

選擇加入現有專案將可讓您瀏覽電腦上的現有專案，並將它加入至解決方案。

## <a name="see-also"></a>另請參閱

- [建立方案和專案 (Windows 上的 Visual Studio)](/visualstudio/ide/creating-solutions-and-projects)
