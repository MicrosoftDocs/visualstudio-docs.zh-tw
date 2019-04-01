---
title: 更新網路型安裝
description: 了解如何使用 --layout 命令來更新網路型 Visual Studio 安裝
ms.date: 2/22/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4f7f7a7297b7cc48b9300c21875af5a0971136e1
ms.sourcegitcommit: 8d453b345c72339c37b489a140dad00b244e6ba4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2019
ms.locfileid: "58475977"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>更新 Visual Studio 的網路型安裝

可以使用最新的產品更新來更新 Visual Studio 的網路安裝配置，這樣一來它就可以同時作為 Visual Studio 最新更新的安裝點，也能維護已部署至用戶端工作站的安裝。

## <a name="how-to-update-a-network-layout"></a>如何更新網路配置

若要重新整理您的網路安裝共用，以便其包含最新的更新，請執行 `--layout` 命令，以累加方式下載更新的套件。

**15.3 中的新功能**：如果您在最初建立網路配置時已選取部分配置，則會儲存這些設定。  任何未來的配置命令都會使用先前的選項，以及您指定的任何新選項 但是如果您要使用舊版本的配置，則應該使用您最初建立網路安裝配置時所使用的相同命令列參數 (亦即，相同的工作負載和語言) 來更新其內容。

如果您在檔案共用上裝載配置，則應該更新該配置的私用複本 (例如 c:\vs2017offline))，然後在下載所有已更新的內容之後，將該複本複製到檔案共用 (例如 \\server\products\VS2017)。 如果不這麼做，則在您更新配置時執行安裝程式的任何使用者，都很有可能無法取得配置的所有內容，因為配置尚未完全更新。

讓我們以一些範例來逐步解說如何在建立後更新配置：

* 首先，以下是如何建立只包含一份英文工作負載的配置範例：

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* 以下是如何該相同的配置更新為較新版本。 您不需要指定任何其他命令列參數。 已儲存先前的設定，並且將供這個配置資料夾中的任何後續配置命令使用。

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout
  ```

* 以下是如何以自動方式將配置更新為較新版本。 配置作業會在新的主控台視窗中執行安裝程序。 此視窗會保持開啟，好讓使用者可以看到最後的結果及可能發生之任何錯誤的摘要。 如果您正以自動方式執行配置作業 (例如讓指令碼定期執行以將配置更新為最新版本)，則使用 `--passive` 參數和處理序將會自動關閉視窗。

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --passive
  ```

* 以下是如何新增額外的工作負載和當地語系化語言  (這個命令會新增 Azure 工作負載)。現在，Managed 桌面和 Azure 都會包含在此配置中。  所有這些工作負載也會包含英文和德文的語言資源。  而且，配置會更新為最新的可用版本。

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > 即使您將所新增選擇性元件包含在[回應檔案](automated-installation-with-response-file.md)的「新增」區段中，更新作業也不會安裝這些元件。 這是因為新增作業不會在更新期間使用。<br>
    > **因應措施**：在升級後執行個別修改作業，以安裝遺漏的元件。

* 最後，以下是如何新增額外的工作負載和當地語系化語言，而不需要更新版本。 (這個命令會新增 ASP.NET 和 Web 工作負載)。現在，Managed 桌面、Azure 以及 ASP.NET 和 Web 工作負載都會包含在此配置中。 所有這些工作負載也會包含英文、德文和法文的語言資源。  不過，執行此命令時，不會將配置更新為最新可用版本。 它會保持現有的版本。

  ```cmd
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="how-to-deploy-an-update-to-client-machines"></a>如何將更新部署至用戶端電腦

根據您網路環境的設定方式，更新可以由企業系統管理員部署或從用戶端電腦起始。

* 使用者可以更新從離線安裝資料夾安裝的 Visual Studio 執行個體：
  * 執行 Visual Studio 安裝程式。
  * 接著，按一下 [更新]。

* 利用兩個不同的命令，系統管理員可以更新 Visual Studio 的用戶端部署，而不需要任何使用者互動：
  * 首先，更新 Visual Studio 安裝程式： <br>```vs_enterprise.exe --quiet --update```
  * 接著，更新 Visual Studio 應用程式本身： <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> 使用 [vswhere.exe 命令](tools-for-managing-visual-studio-instances.md)來識別用戶端電腦上 Visual Studio 現有執行個體的安裝路徑。
>
> [!TIP]
> 如需如何控制顯示更新通知給使用者的詳細資料，請參閱[控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)。

## <a name="how-to-verify-a-layout"></a>配置的驗證方式

使用 `--verify`，對提供的離線快取執行驗證。 它會檢查套件檔案為遺失或無效。 在驗證結束時，會列印遺失檔案和無效檔案的清單。

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

vs_enterprise.exe 可以在 layoutDir 內進行叫用。

> [!NOTE]
> `--verify` 選項所需的一些重要中繼資料檔案必須在配置離線快取中。 如果遺失這些中繼資料檔案，則無法執行 "--verify"，而且安裝程式會產生錯誤。 如果您遇到此錯誤，請將新的離線配置重新建立到不同的資料夾 (或相同的離線快取資料夾)。 若要這麼做，請執行您用來建立初始離線配置的相同配置命令。 例如，`Vs_enterprise.exe --layout <layoutDir>`。

Microsoft 會定期提供 Visual Studio 更新，因此，您建立的新配置可能不是與初始配置相同的版本。

> [!NOTE]
> 驗證僅適用於特定 Visual Studio 次要版本的最新版。 新的版本發行後，驗證即不再適用於同一個次要版本的較舊修補層級版本。

## <a name="how-to-fix-a-layout"></a>如何修正配置

使用 `--fix` 執行與 `--verify` 相同的驗證，同時嘗試修正已識別的問題。 `--fix` 程序需要網際網路連線，因此請先確定您的電腦連線至網際網路，再叫用 `--fix`。

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

vs_enterprise.exe 可以在 layoutDir 內進行叫用。

## <a name="how-to-remove-older-versions-from-a-layout"></a>如何從配置中移除較舊版本

在您執行離線快取的配置更新之後，配置快取資料夾可能有最新 Visual Studio 安裝不再需要的一些過時套件。 您可以使用 `--clean` 選項，從離線快取資料夾中移除過時套件。

若要這麼做，您需要包含這些過時套件之目錄資訊清單的檔案路徑。 您可以在離線配置快取的 [封存] 資料夾中尋找目錄資訊清單。 當您更新配置時，即會將它們儲存在該處。 在 [封存] 資料夾中，有一或多個 "GUID" 具名資料夾，且各包含過時目錄資訊清單。 "GUID" 資料夾數目應該與對您的離線快取進行的更新數目相同。

有一些檔案儲存在每個 "GUID" 資料夾內。 最有趣的兩個檔案是 "catalog.json" 檔案和 "version.txt" 檔案。 "catalog.json" 檔案是您需要傳遞至 `--clean` 選項的過時目錄資訊清單。 其他 version.txt 檔案包含此過時目錄資訊清單的版本。 根據版本號碼，您可以決定是否要從此目錄資訊清單中移除過時套件。 當您瀏覽其他 "GUID" 資料夾時，可以執行相同動作。 在您決定想要清除的目錄之後，請提供這些目錄的檔案路徑來執行 `--clean` 命令。

以下是如何使用 --clean 選項的一些範例：

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

您也可以叫用 &lt;layoutDir&gt; 內的 vs_enterprise.exe。 以下為範例：

```cmd
c:\VS2017Layout\vs_enterprise.exe --layout c:\VS2017Layout --clean c:\VS2017Layout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

當您執行此命令時，安裝程式會分析您的離線快取資料夾，以尋找將移除的檔案清單。 您接著可能會檢閱要刪除的檔案，並確認刪除。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [用於偵測及管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)
* [控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
