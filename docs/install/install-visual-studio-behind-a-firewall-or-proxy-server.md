---
title: "將 Visual Studio 安裝在防火牆或 Proxy 伺服器後方 | Microsoft Docs"
description: 
ms.custom: 
ms.date: 08/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 2bafcbf441d4efd6446e77f619379a665597e063
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2017
---
# <a name="install-visual-studio-behind-a-firewall-or-proxy-server"></a>將 Visual Studio 安裝在防火牆或 Proxy 伺服器後方

Visual Studio 安裝程式會從各種不同的網域及其下載伺服器下載檔案。 此頁面會列出您可能想要在部署指令碼中列入受信任「白名單」的網域 URL。

如果您的環境許可，請考慮同時以 HTTP 和 HTTPS 通訊協定版本新增下列網域。

## <a name="microsoft-domains"></a>Microsoft 網域
| Domain | 用途 |
| ------ | ------- |
| go.microsoft.com | 安裝 URL 解析 |
| aka.ms | 安裝 URL 解析 |
| download.visualstudio.microsoft.com | 安裝套件下載位置 |
| download.microsoft.com | 安裝套件下載位置 |
| download.visualstudio.com | 安裝套件下載位置 |
| dl.xamarin.com | 安裝套件下載位置 |
| visualstudiogallery.msdn.microsoft.com | Visual Studio 延伸模組下載位置 |
| www.visualstudio.com | 文件位置 |
| docs.microsoft.com | 文件位置 |
| msdn.microsoft.com | 文件位置 |
| www.microsoft.com | 文件位置 |
| * windows.net | 登入位置 |
| *.microsoftonline.com | 登入位置 |
| *.live.com | 登入位置 |


## <a name="non-microsoft-domains"></a>非 Microsoft 網域
| Domain | 安裝這些工作負載 |
| ------ | ------- |
| archive.apache.org |  使用 JavaScript 的行動裝置程式開發 <br />(Cordova) |
| cocos2d-x.org | 使用 C++ 的遊戲程式開發 <br />(Cocos) |
| download.epicgames.com | 使用 C++ 的遊戲程式開發 <br />(Unreal Engine) |
| download.oracle.com | 使用 JavaScript 的行動裝置程式開發 <br />(Java SDK) <br /><br />使用 .NET 的行動裝置程式開發 <br />(Java SDK) |
| download.unity3d.com | 使用 Unity 的遊戲程式開發 <br />(Unity) |
| netstorage.unity3d.com | 使用 Unity 的遊戲程式開發 <br /> (Unity) |
| dl.google.com | 使用 JavaScript 的行動裝置程式開發 <br />(Android SDK and NDK, Emulator) <br /><br />使用 .NET 的行動裝置程式開發 <br />(Android SDK and NDK, Emulator) |
| www.incredibuild.com | 使用 C++ 的遊戲程式開發 <br />(IncrediBuild) |
| incredibuildvs2017i.azureedge.net | 使用 C++ 的遊戲程式開發 <br />(IncrediBuild) |
| www.python.org | Python 開發 <br />(Python) <br /><br />資料科學和分析應用程式 <br />(Python) |

## <a name="get-support"></a>取得支援
有時可能會發生一些問題。 如果您的 Visual Studio 安裝失敗，請參閱[針對 Visual Studio 2017 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)頁面。 如果所有疑難排解步驟都沒有幫助，您可以透過即時聊天與我們連絡，以取得安裝協助 (僅限英文)。 如需詳細資訊，請參閱 [Visual Studio 支援頁面](https://www.visualstudio.com/vs/support/#talktous) \(英文\)。

以下是一些支援選項：
* 您可以透過 Visual Studio 安裝程式和 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具來向我們報告產品問題。
* 您可以在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享產品建議。
* 您可以在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)追蹤產品問題，也可以在那裡詢問問題和尋找解答。
* 您也可以透過我們[在 Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與我們以及其他 Visual Studio 開發人員進行互動  (這個選項需要 [GitHub](https://github.com/) 帳戶)。

## <a name="see-also"></a>請參閱
* [安裝 Visual Studio 2017](install-visual-studio.md)
* [使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [命令列參數範例](command-line-parameter-examples.md)
  * [工作負載與元件識別碼參考](workload-and-component-ids.md)
* [建立 Visual Studio 2017 的網路型安裝](create-a-network-installation-of-visual-studio.md)
  * [安裝 Visual Studio 離線安裝所需的憑證](install-certificates-for-visual-studio-offline.md)
* [使用回應檔自動安裝 Visual Studio](automated-installation-with-response-file.md)
* [部署 Visual Studio 時會自動套用產品金鑰](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [設定 Visual Studio 2017 企業部署的預設值](set-defaults-for-enterprise-deployments.md)
* [停用或移動套件快取](disable-or-move-the-package-cache.md)
* [更新 Visual Studio 的網路型安裝](update-a-network-installation-of-visual-studio.md)
* [控制 Visual Studio 2017 部署的更新](controlling-updates-to-visual-studio-deployments.md)
* [用於偵測及管理 Visual Studio 執行個體的工具](tools-for-managing-visual-studio-instances.md)
