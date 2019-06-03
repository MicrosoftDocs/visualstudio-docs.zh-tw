---
title: 在維護基底上時更新 Visual Studio
titleSuffix: ''
description: 了解如何在維護基底上時更新 Visual Studio。
ms.date: 05/22/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: doughall
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8928feffed77f8bfbb3787bd9a20737b9c7b3f9e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66213779"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>在維護基底上時更新 Visual Studio

Visual Studio 2019 將在其[產品生命週期](/visualstudio/productinfo/release-rhythm.md#release-channel-updates)期間進行頻繁的更新。 這些包含兩個次要版本更新 (例如：16.0 至 16.1)，可以包含新功能和元件，以及僅包含重大問題之目標修正程式的服務更新 (例如：16.0.4 至 16.0.5)。 

企業系統管理員可以選擇將其用戶端保留在服務基準上，這可以在下一個服務基準發行後的一年內提供服務更新。 這為開發人員和管理員提供了更大的彈性，可以採用新的功能、錯誤 (bug) 修正，或新的次要更新中所包含的元件。 第一個服務基準是 16.0.x。 如需詳細資訊，請參閱 [Enterprise 與 Professional 客戶的支援選項](/visualstudio/releases/2019/servicing.md#support-options-for-enterprise-and-professional-customers)。

## <a name="how-to-get-onto-a-servicing-baseline"></a>如何進入服務基準

若要開始使用服務基準，請從 [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0) 下載固定版本的 Visual Studio 安裝程式啟動載入器。 這些啟動載入器具有指向該特定版本之產品設定、工作負載和元件的連結。 

> [!NOTE]
> 請小心區別固定版本的啟動載入器和一般的啟動載入器。 一般的啟動載入器會設定為使用 Visual Studio 的最新可用版本。 從 my.visualstudio.com 下載時，它們在檔案名稱中會有數字 (例如：vs_enterprise__123456789-123456789.exe)。

在安裝期間，企業系統管理員必須設定其用戶端以防止它們更新至最新版本。 這可以藉由[變更回應設定檔中的 channelUri 設定](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network)來使用配置或本機資料夾中的通道資訊清單、藉由[透過命令列執行修改 channelUri](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) 來使用不存在的檔案，或藉由[在用戶端系統上設定原則來停用更新](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating)以防止用戶端自我更新。 

### <a name="install-a-servicing-baseline-on-a-network"></a>在網路上安裝服務基準

對於使用網路配置安裝的系統管理員，請修改面配置中 `response.json` 中的 channelUri 值，以使用位於相同資料夾中的 channelmanifest.json。 如需逐步指南，請參閱[控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)。 變更 channelUri 可讓用戶端在版面配置位置中尋找更新。 

### <a name="install-a-servicing-baseline-via-the-internet"></a>透過網際網路安裝服務基準

如果是網際網路型安裝，請將 `--channelUri` 與不存在的通道資訊清單新增至用來啟動安裝程式的命令列。 這會禁止 Visual Studio 使用最新的可用版本進行更新。 請看以下範例：

  ```cmd
   vs_enterprise.exe --channelUri c:\doesnotexist.chman 
  ```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>使用原則設定來停用用戶端更新

控制用戶端更新的另一個選項是[關閉更新通知](controlling-updates-to-visual-studio-deployments.md)。 如果在安裝時未變更 channelUri 值，請使用此選項。 它將禁止用戶端接收指向最新可用版本的連結。 在客戶端上，仍然需要固定版本的啟動載入器來更新到特定版本。

## <a name="how-to-stay-on-a-servicing-baseline"></a>如何保持服務基準

當服務基準有更新時，固定版本的啟動載入器檔案可用於 [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0) 的服務更新。 這些可以在數種案例下使用。

針對透過網路配置進行部署的系統管理員，系統管理員需要更新[版面配置位置](update-a-network-installation-of-visual-studio.md)。 從該位置安裝的用戶端會收到更新通知。 如果需要部署至用戶端更新，請遵循[這些指示](update-a-network-installation-of-visual-studio.md#how-to-deploy-an-update-to-client-machines)。 當修改 'response.json' 以進行更新時，請勿新增額外的工作負載、元件或語言。 在產品更新後，必須以「修改」部署的方式管理這些設定。 

如果是網際網路型安裝，請執行新的固定版本啟動載入器，其中 `--channelUri` 參數指向用戶端上不存在的通道資訊清單。 如果更新是以無訊息或被動模式進行部署，請使用兩個不同的命令：

1. 首先，更新 Visual Studio 安裝程式： <br>```vs_enterprise.exe --quiet --update```
2. 接著，更新 Visual Studio 應用程式本身： <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [用於偵測及管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)
* [如何在回應檔中定義設定](automated-installation-with-response-file.md)
* [控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio 產品生命週期和服務](/visualstudio/releases/2019/servicing/)
