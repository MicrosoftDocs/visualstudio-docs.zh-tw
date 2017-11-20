---
title: "ClickOnce 和應用程式設定 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: fbe35de06ac09c95a045748a5d8ecb379779a20a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-and-application-settings"></a>ClickOnce 和應用程式設定
Windows Form 的應用程式設定可讓您輕鬆地建立、 儲存和維護自訂應用程式和用戶端上的使用者喜好設定。 下列文件說明應用程式設定檔在 ClickOnce 應用程式中的運作方式，以及如何 ClickOnce 移轉設定時使用者升級至下一個版本。  
  
 下列資訊僅適用於預設應用程式設定提供者，<xref:System.Configuration.LocalFileSettingsProvider>類別。 如果您提供自訂提供者，它將其資料的儲存，以及如何升級設定版本之間，將會決定該提供者。 如需有關應用程式設定提供者的詳細資訊，請參閱[應用程式設定架構](/dotnet/framework/winforms/advanced/application-settings-architecture)。  
  
## <a name="application-settings-files"></a>應用程式設定檔  
 應用程式設定會使用兩個檔案：*應用程式*。.exe.config，而且 user.config，其中*應用程式*是 Windows Forms 應用程式的名稱。 user.config 會建立在用戶端第一次應用程式儲存使用者範圍的設定。 *應用程式*。.exe.config，相反地，如果會存在部署之前，先定義設定的預設值。 Visual Studio 會自動包含此檔案，當您使用其**發行**命令。 如果您建立 ClickOnce 應用程式使用 Mage.exe 或 MageUI.exe 中，您必須確定這個檔案隨附於應用程式的其他檔案，當您填入應用程式資訊清單。  
  
 在 Windows Form 應用程式中不使用 ClickOnce 應用程式的部署*應用程式*。.exe.config 檔案儲存在應用程式目錄中，而此 user.config 檔則會儲存在使用者的**Documents and Settings**資料夾。 在 ClickOnce 應用程式中，*應用程式*。.exe.config 都位於 ClickOnce 應用程式快取內的應用程式目錄中，而 user.config 位於該應用程式的 ClickOnce 資料目錄。  
  
 部署您的應用程式的方式，不論應用程式設定可確保安全的讀取存取權*應用程式*。.exe.config，而且 user.config 安全的讀取/寫入存取。  
  
 在 ClickOnce 應用程式，ClickOnce 快取的大小限制的應用程式設定所使用的設定檔案大小。 如需詳細資訊，請參閱[ClickOnce 快取概觀](../deployment/clickonce-cache-overview.md)。  
  
## <a name="version-upgrades"></a>版本升級  
 就像是 ClickOnce 應用程式的每個版本與所有其他版本隔離，應用程式設定 ClickOnce 應用程式是為其他版本以及設定與隔離。 當您的使用者升級至新版的應用程式時，應用程式設定會比較最近 （最高編號） 版本的設定與更新的版本並合併成一組新的設定檔設定所提供。  
  
 下表描述應用程式設定如何決定要複製的設定。  
  
|變更類型|升級動作|  
|--------------------|--------------------|  
|設定新增至*應用程式*。.exe.config|新的設定會合併到目前的版本*應用程式*。.exe.config|  
|設定從移除*應用程式*。.exe.config|目前的版本中移除舊的設定*應用程式*。.exe.config|  
|設定的預設值已變更;本機設定仍然設為原始預設值在 user.config|設定合併到新的預設值的目前版本的 user.config 做為值|  
|設定的預設值已變更;設定設定為非預設值在 user.config|設定合併到目前的版本 user.config 與保留的非預設值|  
  
 如果您已建立您自己的應用程式設定包裝函式類別，並想要自訂更新邏輯，您可以覆寫<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A>方法。  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce 和漫遊設定  
 ClickOnce 不適用於漫遊設定，可讓您遵循您在電腦之間網路上的設定檔。 如果您需要漫遊設定，您必須要實作應用程式設定提供者儲存設定，透過網路或開發您自己的自訂設定類別，在遠端電腦上儲存設定。 如需設定提供者中的詳細資訊，請參閱[應用程式設定架構](/dotnet/framework/winforms/advanced/application-settings-architecture)。  
  
## <a name="see-also"></a>另請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)   
 [應用程式設定概觀](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [ClickOnce 快取概觀](../deployment/clickonce-cache-overview.md)   
 [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)