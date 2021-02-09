---
title: ClickOnce 和應用程式設定 |Microsoft Docs
description: 瞭解應用程式佈建檔在 ClickOnce 應用程式中的運作方式，以及 ClickOnce 如何在使用者升級到下一個版本時遷移設定。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96491dc192b6578abd725d5d69b7c9093e92b20c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896386"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce 和應用程式設定
Windows Forms 的應用程式設定可讓您輕鬆地在用戶端上建立、儲存和維護自訂的應用程式和使用者喜好設定。 下列檔說明應用程式佈建檔在 ClickOnce 應用程式中的運作方式，以及 ClickOnce 如何在使用者升級到下一個版本時遷移設定。

 下列資訊僅適用于預設的應用程式設定提供者，也就是 <xref:System.Configuration.LocalFileSettingsProvider> 類別。 如果您提供自訂提供者，該提供者將會決定其儲存資料的方式，以及它如何在版本之間升級其設定。 如需應用程式設定提供者的詳細資訊，請參閱 [應用程式設定架構](/dotnet/framework/winforms/advanced/application-settings-architecture)。

## <a name="application-settings-files"></a>應用程式佈建檔案
 應用程式設定會使用兩個檔案： *\<app>.exe.config* 和 *user.config*，其中 *應用* 程式是您 Windows Forms 應用程式的名稱。 當應用程式第一次儲存使用者範圍的設定時，會在用戶端上建立 *user.config* 。 相反地， *\<app>.exe.config*，則在部署之前，如果您定義了設定的預設值，就會存在。 當您使用 [ **發行** ] 命令時，Visual Studio 將會自動包含此檔案。 如果您使用 *Mage.exe* 或 *MageUI.exe* 來建立 ClickOnce 應用程式，您必須在填入應用程式資訊清單時，確定此檔案包含在應用程式的其他檔案中。

 在未使用 ClickOnce 部署的 Windows Forms 應用程式中，應用程式的 *\<app>.exe.config* 檔會儲存在應用程式目錄中，而 *user.config* 檔則會儲存在使用者的 [檔 **和設定**] 資料夾中。 在 ClickOnce 應用程式中， *\<app>.exe.config* 存在於 clickonce 應用程式快取內的應用程式目錄中， *user.config* 存在於該應用程式的 clickonce 資料目錄中。

 無論您如何部署應用程式，應用程式設定都能確保 *\<app>.exe.config* 的安全讀取存取，以及 *user.config* 的安全讀取/寫入存取權。

 在 ClickOnce 應用程式中，應用程式設定所使用的配置檔案大小受限於 ClickOnce 快取的大小。 如需詳細資訊，請參閱 ClickOnce 快取 [總覽](../deployment/clickonce-cache-overview.md)。

## <a name="version-upgrades"></a>版本升級
 如同每個版本的 ClickOnce 應用程式與其他所有版本隔離，ClickOnce 應用程式的應用程式設定也會與其他版本的設定隔離。 當您的使用者升級至較新版本的應用程式時，應用程式設定會將最近 (的最高編號) 版本的設定與更新版本提供的設定進行比較，並將設定合併到新的設定檔集。

 下表描述應用程式設定如何決定要複製的設定。

|變更類型|升級動作|
|--------------------|--------------------|
|將設定新增至 *\<app>.exe.config*|新的設定會合並到目前版本的 *\<app>.exe.config*|
|從 *\<app>.exe.config* 移除的設定|舊的設定會從目前版本的 *\<app>.exe.config* 中移除|
|設定的預設值已變更;本機設定仍設為 *user.config* 中的原始預設值|此設定會合並到目前版本的 *user.config* 中，並以新的預設值作為值|
|設定的預設值已變更;*user.config* 中設定為非預設值|此設定會合並到目前版本的 *user.config* ，並保留非預設值|

如果您已建立自己的應用程式設定包裝函式類別，而且想要自訂更新邏輯，則可以覆寫 <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> 方法。

## <a name="clickonce-and-roaming-settings"></a>ClickOnce 和漫遊設定
 ClickOnce 不適用於漫遊設定，可讓您的設定檔在網路上的電腦上跟著使用。 如果您需要漫遊設定，您將需要執行可透過網路儲存設定的應用程式設定提供者，或開發您自己的自訂設定類別以將設定儲存在遠端電腦上。 如需設定提供者的詳細資訊，請參閱 [應用程式設定架構](/dotnet/framework/winforms/advanced/application-settings-architecture)。

## <a name="see-also"></a>另請參閱
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [應用程式設定總覽](/dotnet/framework/winforms/advanced/application-settings-overview)
- [ClickOnce 快取概觀](../deployment/clickonce-cache-overview.md)
- [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)