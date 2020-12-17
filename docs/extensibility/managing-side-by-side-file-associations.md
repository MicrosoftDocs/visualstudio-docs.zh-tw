---
title: 管理並存檔案關聯 |Microsoft Docs
description: 如果您的 VSPackage 提供檔案關聯，請決定如何處理特定版本的 Visual Studio 開啟檔案的並存安裝。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 477afbd5bc4586d8c46db11b036364f8058133b0
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616340"
---
# <a name="manage-side-by-side-file-associations"></a>管理並存檔案關聯

如果您的 VSPackage 提供檔案關聯，您必須決定如何處理並存安裝，其中應叫用特定版本的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 來開啟檔案。 不相容的檔案格式會複合問題。

使用者預期新版本的產品會與舊版相容，因此可以在新版本中載入現有的檔案，而不會遺失資料。 在理想的情況下，您的 VSPackage 可以載入和儲存舊版的檔案格式。 如果不是 true，您應該提供將檔案格式升級為新版本的 VSPackage。 這種方法的缺點是，升級的檔案無法在舊版中開啟。

若要避免這個問題，您可以在檔案格式變成不相容時變更延伸模組。 例如，第1版的 VSPackage 可以使用副檔名 *mypkg10*，而第2版可以使用擴充功能 *mypkg20*。 這項差異會識別開啟特定檔案的 VSPackage。 如果您將較新的 Vspackage 新增至與舊副檔名相關聯的程式清單，使用者可以在檔案上按一下滑鼠右鍵，然後選擇在較新的 VSPackage 中開啟該檔案。 屆時，您的 VSPackage 可以提供將檔案升級為新格式或開啟檔案，並維持與舊版 VSPackage 的相容性。

> [!NOTE]
> 您可以結合這些方法。 例如，您可以藉由載入較舊的檔案，並在使用者儲存檔案格式時提供升級檔案格式，來提供回溯相容性。

## <a name="face-the-problem"></a>面對問題

如果您想要讓多個並存 Vspackage 使用相同的擴充功能，您必須選擇 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 與延伸模組相關聯的版本。 以下是兩個替代方案：

- 在使用者電腦上安裝的最新版本中開啟檔案 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

   在這個方法中，您的安裝程式會負責判斷的最新版本， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 並將它包含在針對檔案關聯所撰寫的登錄專案中。 在 Windows Installer 套件中，您可以加入自訂動作來設定屬性，以指出的最新版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

  > [!NOTE]
  > 在此內容中，「最新」表示「最新支援的版本」。 這些安裝程式專案將不會自動偵測後續的版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 偵測 [系統需求](../extensibility/internals/detecting-system-requirements.md) 的專案，以及在 [安裝後必須執行的命令](../extensibility/internals/commands-that-must-be-run-after-installation.md) 中的專案，類似于此處顯示的專案，而且需要支援其他版本的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

   CustomAction 資料表中的下列資料列，會將 DEVENV_EXE_LATEST 屬性設定為 AppSearch 和 RegLocator 資料表所設定的屬性 [，這些命令必須在安裝之後執行](../extensibility/internals/commands-that-must-be-run-after-installation.md)。 InstallExecuteSequence 資料表中的資料列會在執行順序初期排程自訂動作。 [條件] 資料行中的值可讓邏輯運作：

  - 如果是唯一的版本，則 Visual Studio .NET 2002 是最新版本。

  - Visual Studio .NET 2003 只有存在且不存在時才是最新版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 是最新版本（如果它是唯一版本的話）。

    最後的結果是，DEVENV_EXE_LATEST 包含 devenv.exe 最新版本的路徑。

  **CustomAction 決定最新版本 Visual Studio 的資料表資料列**

  |動作|類型|來源|目標|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **InstallExecuteSequence 決定最新版本 Visual Studio 的資料表資料列**

  |動作|條件|順序|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002，而不是 (DEVENV_EXE_2003 或 DEVENV_EXE_2005) |410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 而不是 DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   您可以使用 Windows Installer 封裝之登錄表中的 DEVENV_EXE_LATEST 屬性，來寫入 **HKEY_CLASSES_ROOT *ProgId* ShellOpenCommand** 索引鍵的預設值 [DEVENV_EXE_LATEST] "%1"

- 執行可讓您從可用的 VSPackage 版本中獲得最佳選擇的共用啟動器程式。

   開發人員 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 選擇這種方法，來處理許多版本所產生的多個解決方案和專案格式的複雜需求 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 在此方法中，您會將啟動器程式註冊為擴充處理常式。 啟動器會檢查檔案，並決定哪一個版本的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和您的 VSPackage 可以處理該特定檔案。 例如，如果使用者開啟的檔案是由特定版本的 VSPackage 所儲存，則啟動器可以在相符的版本中啟動該 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 此外，使用者也可以將啟動器設定為一律啟動最新版本。 啟動器也可以提示使用者升級檔案的格式。 如果檔案的格式包含版本號碼，則啟動器可能會通知使用者，如果檔案格式來自于一或多個已安裝的 Vspackage 版本。

   啟動器應該位於與 VSPackage 所有版本共用的 Windows Installer 元件中。 此程式可確保一律會安裝最新版本，而且在卸載所有版本的 VSPackage 之前都不會移除。 如此一來，即使已卸載其中一個版本的 VSPackage，仍會保留啟動器元件的檔案關聯和其他登錄專案。

## <a name="uninstall-and-file-associations"></a>卸載和檔案關聯

卸載為檔案關聯寫入登錄專案的 VSPackage 會移除檔案關聯。 因此，此延伸模組沒有相關聯的程式。 Windows Installer 不會「復原」已在安裝 VSPackage 時新增的登錄專案。 以下是修正使用者檔案關聯的一些方法：

- 如先前所述，使用共用啟動器元件。

- 指示使用者執行使用者想要擁有檔案關聯之 VSPackage 版本的修復。

- 提供可重寫適當登錄專案的個別可執行程式。

- [提供設定選項] 頁面或對話方塊，可讓使用者選擇檔案關聯和回收遺失的關聯。 指示使用者在卸載之後執行。

## <a name="see-also"></a>另請參閱

- [註冊並存部署的副檔名](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [註冊副檔名的動詞](../extensibility/registering-verbs-for-file-name-extensions.md)
