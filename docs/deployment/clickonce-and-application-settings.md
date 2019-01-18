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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40077a30a49842187c24b4cf8b0cba18b3d0a46a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850962"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce 和應用程式設定
Windows Forms 的應用程式設定可讓您輕鬆地建立、 儲存及維護自訂應用程式和用戶端上的使用者喜好設定。 下列文件會描述應用程式設定檔在 ClickOnce 應用程式中的運作方式，以及 ClickOnce 如何移轉設定，當使用者升級至下一個版本。  
  
 下列資訊僅適用於預設應用程式設定提供者， \<xref:System.Configuration.LocalFileSettingsProvider > 類別。 如果您提供自訂提供者時，它會儲存其資料的方式，以及如何升級設定版本之間，會決定該提供者。 如需有關應用程式設定提供者的詳細資訊，請參閱 <<c0> [ 應用程式設定架構](/dotnet/framework/winforms/advanced/application-settings-architecture)。  
  
## <a name="application-settings-files"></a>應用程式設定檔  
 應用程式設定會使用兩個檔案： *\<應用程式 >。 .exe.config*並*user.config*，其中*應用程式*是 Windows Forms 應用程式的名稱。 *user.config*建立在您的應用程式會儲存使用者範圍設定用戶端第一次。 *\<應用程式 >。 .exe.config*，相較之下，將會在部署之前如果存在定義設定的預設值。 Visual Studio 會自動包含此檔案，當您使用其**發佈**命令。 如果您建立 ClickOnce 應用程式使用*Mage.exe*或是*MageUI.exe*，您必須先確定此檔案是包含應用程式的其他檔案，當您填入您的應用程式資訊清單。  
  
 不使用 ClickOnce 部署，應用程式的 Windows Forms 應用程式中*\<應用程式 >。 .exe.config*檔案會儲存在應用程式目錄中，雖然*user.config*儲存檔案在使用者的**Documents and Settings**資料夾。 在 ClickOnce 應用程式中， *\<應用程式 >。 .exe.config*居住在 ClickOnce 應用程式快取內的應用程式目錄並*user.config*位於 ClickOnce 資料目錄該應用程式。  
  
 不論您如何部署您的應用程式，應用程式設定可確保安全的讀取存取權*\<應用程式 >。 .exe.config*，和安全的讀取/寫入存取權*user.config*。  
  
 在 ClickOnce 應用程式中使用的應用程式設定的組態檔的大小會受到 ClickOnce 快取大小。 如需詳細資訊，請參閱 < [ClickOnce 快取概觀](../deployment/clickonce-cache-overview.md)。  
  
## <a name="version-upgrades"></a>版本升級  
 如同每個版本的 ClickOnce 應用程式是與所有其他版本隔離，ClickOnce 應用程式的應用程式設定會與隔離以及其他版本的設定。 當您的使用者升級至較新版的應用程式時，應用程式設定就會比較與合併成一組新的設定檔設定的更新的版本所提供的最新 （最高編號） 版本的設定。  
  
 下表說明如何應用程式設定會決定要複製的設定。  
  
|變更類型|升級動作|  
|--------------------|--------------------|  
|設定新增至*\<應用程式 >。 .exe.config*|新的設定會合併到目前的版本*\<應用程式 >。 .exe.config*|  
|設定移除了*\<應用程式 >。 .exe.config*|目前的版本中移除舊的設定*\<應用程式 >。 .exe.config*|  
|設定的預設值已變更;中的原始預設值仍然設定本機設定*user.config*|此設定會合併到目前的版本*user.config*與新的預設值，做為值|  
|設定的預設值已變更;設定中的非預設*user.config*|此設定會合併到目前的版本*user.config*保留為非預設值|  
  
如果您已建立您自己的應用程式設定包裝函式類別，並想要自訂更新邏輯，您可以覆寫\<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A > 方法。  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce 和漫遊設定  
 ClickOnce 不適用於漫遊設定，可讓您依照您跨電腦在網路上的設定檔。 如果您需要漫遊設定，您必須實作應用程式設定提供者可透過網路、 儲存設定，或是開發您自己的自訂設定類別，用於儲存在遠端電腦上的設定。 如需在 設定提供者的詳細資訊，請參閱[應用程式設定架構](/dotnet/framework/winforms/advanced/application-settings-architecture)。  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [應用程式設定概觀](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [ClickOnce 快取概觀](../deployment/clickonce-cache-overview.md)   
 [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)