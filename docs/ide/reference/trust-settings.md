---
title: 檔案和資料夾的信任設定
description: 學習如何變更檔案和資料夾的信任設定，以保持 Visual Studio 的安全。
author: 2percentsilk
ms.author: allisb
ms.date: 09/05/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: 492a94962d255a9d18dcabdababf7fa6a540ada1
ms.sourcegitcommit: 935e1388281df0f04147802606b5cb7f513d45ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2020
ms.locfileid: "88197392"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>設定檔案和資料夾的信任設定

在打開具有 [Web 標記](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85))的專案之前，Visual Studio 會提示使用者核准。 為了提高安全性，您也可以設定 Visual Studio，使其在打開具有 Web 屬性標記，或者未指定為「信任」** 的任何檔案或資料夾之前，提示使用者核准。 根據預設，會停用檔案與資料夾的檢查。

> [!WARNING]
> 在核准檔案、資料夾或解決方案之前，您仍然應該確認其來源是信任的人員或信任的位置。

## <a name="configure-trust-settings"></a>設定信任設定

若要變更信任設定，請遵循下列步驟：

1. 開啟 [**工具**  >  ] [**選項**  >  ] [**信任設定**]，然後選取右窗格中的 [**設定信任設定**] 連結。

2. 選擇您想用於檔案和資料夾的檢查層級。 您可以讓每一項的檢查各不相同。 可用選項包括：

   * [沒有驗證]****：Visual Studio 不會執行任何檢查。

   * [確認 Web 屬性標記]****：如果檔案或資料夾具有 Web 屬性標記，Visual Studio 會封鎖並要求提供開啟的權限。

   * [確認是否為信任的路徑]****：如果檔案或資料夾的路徑不在 [信任路徑]**** 清單中，Visual Studio 會封鎖並要求提供開啟的權限。

   ![信任驗證選項](media/trust-settings.png)

## <a name="add-trusted-paths"></a>新增信任路徑

若要新增信任路徑，請遵循下列步驟：

1. 開啟 [**工具**  >  ] [**選項**  >  ] [**信任設定**]，然後選取右窗格中的 [**設定信任設定**] 連結。

2. 按一下 [信任設定]**** 對話方塊中的 [新增]****，然後選取 [檔案]**** 或 [資料夾]****。

3. 瀏覽並選取您想要新增至信任清單的檔案或資料夾。

   檔案或資料夾的路徑會出現在 [信任路徑]**** 清單中。

   ![已新增信任路徑](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>移除信任路徑

若要移除信任路徑，請遵循下列步驟：

1. 開啟 [**工具**  >  ] [**選項**  >  ] [**信任設定**]，然後選取右窗格中的 [**設定信任設定**] 連結。

2. 在 [信任路徑]**** 清單中選取您想要移除的路徑，然後按一下 [移除]****。

   > [!TIP]
   > 若要選取多個項目，請在選取路徑的同時按住 **Shift**。

   選取的路徑會從 [信任路徑]**** 清單移除。
