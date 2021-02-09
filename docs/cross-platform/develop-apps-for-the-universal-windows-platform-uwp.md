---
title: 開發適用於通用 Windows 平台 (UWP) 的應用程式
description: 瞭解如何使用 Visual Studio 和通用 Windows 平臺開發工具來建立應用程式。
ms.custom: SEO-VS-2020
ms.date: 10/24/2017
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 906097e0356922cdcc5afbabb1771348962ea4ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859498"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>開發適用於通用 Windows 平台 (UWP) 的應用程式

通用 Windows 平台和單一 Windows 核心可讓您在任何 Windows 10 裝置上執行相同的應用程式 (包括手機和桌上型電腦)。 您可以使用 Visual Studio 和通用 Windows 應用程式開發工具，來建立這些通用 Windows 應用程式。

![通用 Windows 平台](../cross-platform/media/uwp_coreextensions.png)

在 Windows 10 手機、Windows 10 桌上型電腦或 Xbox 上執行您的應用程式。 全部使用相同的應用程式套件！ 有了 Windows 10 單一整合核心，一個應用程式套件可以在所有平台上執行。 我們提供適用於多種平台的延伸模組 SDK，您可將其新增至應用程式以利用平台專屬行為。 例如，手機的擴充功能 SDK 會處理在 Windows 手機上按下返回鍵的行為。 如果您在專案中參考延伸模組 SDK，只要新增執行階段檢查，就能測試該平台是否可以使用這個 SDK。 因此，您可以針對每一個平台使用相同的應用程式套件！

**Windows 核心是什麼？**

這是第一次 Windows 在重整後擁有一個所有 Windows 10 平台通用的核心。 這個核心 (Core) 包含一個通用來源、一個通用 Windows 核心 (Kernel)、一個檔案 I/O 堆疊，還有一個應用程式模型。 針對 UI，只有一個 XAML UI 架構和一個 HTML UI 架構。 既然應用程式能輕鬆地在不同的 Windows 10 裝置上執行，您就可以安心建立更棒的應用程式。

**通用 Windows 平台到底是什麼？**

通用 Windows 平台其實就是合約和版本的集合。 該集合可讓您設定要執行應用程式的目標。 現在，您再也不用鎖定一種作業系統目標，而可以將一或多個裝置系列設為目標。 如需詳細資訊，請參閱[通用 Windows 平台簡介](/windows/uwp/get-started/universal-application-platform-guide)。

## <a name="requirements"></a>規格需求

通用 Windows 應用程式開發工具隨附模擬器，可供您查看應用程式在不同裝置上的外觀。 如果您要使用這些模擬器，您需要在實體電腦上安裝這個軟體。 這部實體機器必須執行 Windows 8.1 (x64) Professional Edition (含) 以上版本，並具備支援用戶端 Hyper-V 和第二層位址轉譯 (SLAT) 的處理器。 如果在虛擬機器上安裝 Visual Studio，則無法使用模擬器。

以下是您需要的軟體清單：

::: moniker range="vs-2017"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows)。 Visual Studio 2017 只支援在 Windows 10 上開發 UWP。 如需詳細資料，請參閱 Visual Studio 的[平台目標](/visualstudio/productinfo/vs2017-compatibility-vs)和[系統需求](/visualstudio/productinfo/vs2017-system-requirements-vs)。

- [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)。 您也需要選用的通用 Windows 平台開發工作負載。

     ![UWP 工作負載](media/uwp_workload.png)

::: moniker-end

::: moniker range="vs-2019"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows)。 Visual Studio 2019 只支援在 Windows 10 上開發 UWP。 如需詳細資料，請參閱 Visual Studio 的[平台目標](/visualstudio/releases/2019/compatibility/)和[系統需求](/visualstudio/releases/2019/system-requirements/)。

- [Visual Studio](https://visualstudio.microsoft.com/downloads)。 您也需要選用的通用 Windows 平台開發工作負載。

     ![UWP 工作負載](media/uwp_workload.png)

::: moniker-end

安裝這個軟體之後，您需要啟用 Windows 10 裝置以進行開發。 請參閱[啟用您的裝置以用於開發](/windows/uwp/get-started/enable-your-device-for-development)。 您不再需要取得每部 Windows 10 裝置的開發人員授權。

## <a name="universal-windows-apps"></a>通用 Windows 應用程式

從 C#、Visual Basic、C++ 或 JavaScript 中，選擇您慣用的開發語言，以建立適用於 Windows 10 裝置的通用 Windows 平台應用程式。 請參閱[建立您的第一個應用程式](/windows/uwp/get-started/your-first-app)，或觀看 [Tools for Windows 10 Overview](https://channel9.msdn.com/Series/ConnectOn-Demand/229) (Windows 10 工具概觀) 影片。

如果您已使用 Visual Studio 2015 建立現有的 Windows 市集 8.1 應用程式、Windows Phone 8.1 應用程式或通用 Windows 應用程式，則需要移轉這些應用程式，以使用最新版的通用 Windows 平台。 請參閱[從 Windows 執行階段 8 移至 UWP](/windows/uwp/porting/w8x-to-uwp-root)。

建立好您的通用 Windows 應用程式之後，您必須封裝應用程式以在 Windows 10 裝置上進行安裝，或提交至 Windows 市集。 請參閱[封裝應用程式](/windows/uwp/packaging/index)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的跨平台行動裝置應用程式開發](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
