---
title: ClickOnce 和應用程式設定 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a72b5bc3f3645d9af1008f2c178ab285e8b45449
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184129"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce 和應用程式設定
Windows Forms 的應用程式設定可讓您輕鬆地在用戶端上建立、儲存及維護自訂應用程式和使用者喜好設定。 下列檔描述應用程式佈建檔在 ClickOnce 應用程式中的使用方式，以及 ClickOnce 如何在使用者升級到下一個版本時遷移設定。

 下列資訊僅適用于預設的應用程式設定提供者（ <xref:System.Configuration.LocalFileSettingsProvider> 類別）。 如果您提供自訂提供者，該提供者會決定它儲存其資料的方式，以及它如何在版本之間升級其設定。 如需應用程式設定提供者的詳細資訊，請參閱[應用程式設定架構](/dotnet/framework/winforms/advanced/application-settings-architecture)。

## <a name="application-settings-files"></a>應用程式佈建檔案
 應用程式設定會取用兩個檔案： * \<app> .exe. config*和*app.config*，其中*應用*程式是 Windows Forms 應用程式的名稱。 當您的應用程式第一次儲存使用者範圍的設定時，會在用戶端上建立*user .config* 。 相較之下，如果您定義設定的預設值，則* \<app> .exe .config*會在部署之前存在。 當您使用其**Publish**命令時，Visual Studio 將會自動包含此檔案。 如果您使用*mage.exe*或*mageui.exe*建立 ClickOnce 應用程式，則在填入應用程式資訊清單時，您必須確定此檔案包含在應用程式的其他檔案中。

 在未使用 ClickOnce 部署的 Windows Forms 應用程式中，應用程式的* \<app> .exe .config*檔案會儲存在應用程式目錄中，而*使用者 .config*檔案則會儲存在使用者的 [**檔和設定**] 資料夾中。 在 ClickOnce 應用程式中， * \<app> .exe*是存在於 clickonce 應用程式快取內的應用程式目錄中，而*使用者 .config*則位於該應用程式的 clickonce 資料目錄中。

 無論您如何部署應用程式，應用程式設定都會確保對* \<app> .exe*的安全讀取權限，以及對*user .config*的安全讀取/寫入存取權。

 在 ClickOnce 應用程式中，應用程式設定所使用的配置檔案大小會受到 ClickOnce 快取的大小所限制。 如需詳細資訊，請參閱[ClickOnce cache 總覽](../deployment/clickonce-cache-overview.md)。

## <a name="version-upgrades"></a>版本升級
 就像 ClickOnce 應用程式的每個版本都與所有其他版本隔離，ClickOnce 應用程式的應用程式設定也會與其他版本的設定隔離。 當您的使用者升級至較新版本的應用程式時，應用程式設定會比較最新（最高編號）版本的設定與更新版本提供的設定，並將設定合併成一組新的設定檔案。

 下表描述應用程式設定如何決定要複製哪些設定。

|變更類型|升級動作|
|--------------------|--------------------|
|已新增至* \<app> .exe .config*的設定|新的設定會合並到目前版本的* \<app> .exe .config*|
|已從* \<app> .exe .config*移除設定|舊的設定會從目前版本的* \<app> .exe .config*中移除|
|設定的預設值已變更;*user .config*中的本機設定仍然設定為原始的預設值|此設定會合並到目前版本的*使用者 .config*中，新的預設值為|
|設定的預設值已變更;*user .config*中的設定設為非預設值|此設定會合並到目前版本的*使用者 .config*中，並保留非預設值|

如果您已建立自己的應用程式設定包裝函式類別，而且想要自訂更新邏輯，您可以覆寫 <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> 方法。

## <a name="clickonce-and-roaming-settings"></a>ClickOnce 和漫遊設定
 ClickOnce 無法與漫遊設定搭配使用，這可讓您的設定檔在網路上的電腦之間進行追蹤。 如果您需要漫遊設定，您需要執行可透過網路儲存設定的應用程式設定提供者，或是開發您自己的自訂設定類別，以便在遠端電腦上儲存設定。 如需設定提供者的詳細資訊，請參閱[應用程式設定架構](/dotnet/framework/winforms/advanced/application-settings-architecture)。

## <a name="see-also"></a>另請參閱
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [應用程式設定概觀](/dotnet/framework/winforms/advanced/application-settings-overview)
- [ClickOnce 快取概觀](../deployment/clickonce-cache-overview.md)
- [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)