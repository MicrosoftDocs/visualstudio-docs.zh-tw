---
title: ClickOnce 和應用程式設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 29f51960ad953318c8d9de749f28f684128e52ef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176972"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce 和應用程式設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Forms 的應用程式設定可讓您輕鬆地建立、 儲存及維護自訂應用程式和用戶端上的使用者喜好設定。 下列文件會描述應用程式設定檔在 ClickOnce 應用程式中的運作方式，以及 ClickOnce 如何移轉設定，當使用者升級至下一個版本。  
  
 下列資訊僅適用於預設應用程式設定提供者，<xref:System.Configuration.LocalFileSettingsProvider>類別。 如果您提供自訂提供者時，它會儲存其資料的方式，以及如何升級設定版本之間，會決定該提供者。 如需有關應用程式設定提供者的詳細資訊，請參閱 <<c0> [ 應用程式設定架構](http://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562)。  
  
## <a name="application-settings-files"></a>應用程式設定檔  
 應用程式設定會使用兩個檔案：*應用程式*.exe.config 和 user.config，其中*應用程式*是 Windows Forms 應用程式的名稱。 user.config 會建立在您的應用程式會儲存使用者範圍設定用戶端第一次。 *應用程式*.exe.config，相較之下，將會在部署之前如果存在定義設定的預設值。 Visual Studio 會自動包含此檔案，當您使用其**發佈**命令。 如果您建立 ClickOnce 應用程式使用 Mage.exe 或 MageUI.exe 中，您必須確定此檔案會包含您的應用程式的其他檔案，當您填入您的應用程式資訊清單。  
  
 不使用 ClickOnce 部署，應用程式的 Windows Forms 應用程式中*應用程式*。 而 user.config 檔案則會儲存在使用者的將會儲存在應用程式目錄的 exe.config 檔**Documents and Settings**資料夾。 在 ClickOnce 應用程式中，*應用程式*.exe.config 居住在 ClickOnce 應用程式快取內的應用程式目錄和位於該應用程式的 ClickOnce 資料目錄的 user.config。  
  
 不論您如何部署您的應用程式，應用程式設定可確保安全的讀取存取權*應用程式*.exe.config，而且 user.config 安全的讀取/寫入存取。  
  
 在 ClickOnce 應用程式中使用的應用程式設定的組態檔的大小會受到 ClickOnce 快取大小。 如需詳細資訊，請參閱 < [ClickOnce 快取概觀](../deployment/clickonce-cache-overview.md)。  
  
## <a name="version-upgrades"></a>版本升級  
 如同每個版本的 ClickOnce 應用程式是與所有其他版本隔離，ClickOnce 應用程式的應用程式設定會與隔離以及其他版本的設定。 當您的使用者升級至較新版的應用程式時，應用程式設定就會比較與合併成一組新的設定檔設定的更新的版本所提供的最新 （最高編號） 版本的設定。  
  
 下表說明如何應用程式設定會決定要複製的設定。  
  
|變更類型|升級動作|  
|--------------------|--------------------|  
|設定新增至*應用程式*.exe.config|新的設定會合併到目前的版本*應用程式*.exe.config|  
|設定移除了*應用程式*.exe.config|目前的版本中移除舊的設定*應用程式*.exe.config|  
|設定的預設值已變更;本機設定仍然設定為原始預設值在 user.config|此設定時，會合併到新的預設值的目前版本的 user.config 上，做為值|  
|設定的預設值已變更;設定設定為非預設在 user.config|設定保留為非預設值合併到目前的版本 user.config|  
  
 如果您已建立您自己的應用程式設定包裝函式類別，並想要自訂更新邏輯，您可以覆寫<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A>方法。  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce 和漫遊設定  
 ClickOnce 不適用於漫遊設定，可讓您依照您跨電腦在網路上的設定檔。 如果您需要漫遊設定，您必須實作應用程式設定提供者可透過網路、 儲存設定，或是開發您自己的自訂設定類別，用於儲存在遠端電腦上的設定。 如需在 設定提供者的詳細資訊，請參閱[應用程式設定架構](http://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562)。  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [應用程式設定概觀](http://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [ClickOnce 快取概觀](../deployment/clickonce-cache-overview.md)   
 [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)



