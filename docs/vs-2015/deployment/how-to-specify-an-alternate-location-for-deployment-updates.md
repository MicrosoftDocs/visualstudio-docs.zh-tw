---
title: 如何:為部署更新指定備用位置 |微軟文件
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b6388833e6574fc1d631d391fa7b67d5f0a3372
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037216"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>如何：指定部署更新的其他位置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

最初可以從[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]CD 或檔共享安裝應用程式,但應用程式必須檢查 Web 上的定期更新。 您可以為部署清單中的更新指定備用位置,以便應用程式可以在初始安裝後從 Web 進行更新。  
  
> [!NOTE]
> 必須將應用程式設定為在本地安裝才能使用此功能。 有關詳細資訊,請參閱[演練:手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 此外,如果從網路安裝[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式,則設置備用位置會導致[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]將該位置用於初始安裝和所有後續更新。 如果在本地安裝應用程式(例如,從CD),則使用原始媒體執行初始安裝,並且所有後續更新都將使用備用位置。  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>使用 MageUI.exe(基於 Windows 表單的實用程式)指定更新的備用位置  
  
1. 開啟 .NET 框架指令提示符並鍵入:  
  
     **mageui.exe**  
  
2. 在 **「檔案**」選單上,選擇 **「打開」** 以開啟應用程式的部署清單。  
  
3. 選取 [部署選項]**** 索引標籤。  
  
4. 在名為 **「啟動位置」** 的文字框中,輸入包含應用程式更新的部署清單的目錄的網址。  
  
5. 保存部署清單。  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>使用 Mage.exe 指定更新的備用位置  
  
1. 開啟 .NET Framework 命令提示字元。  
  
2. 使用以下命令設置更新位置。 在此示例中 **,HelloWorld.exe.應用程式**是[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]應用程式清單的路徑,該清單始終具有 .`http://adatum.com/Update/Path`應用程式擴展,並且[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]是檢查應用程式更新的 URL。  
  
     **馬age - 更新HelloWorld.exe.應用程式\/-提供者 Url http: /adatum.com/Update/Path**  
  
3. 儲存檔案。  
  
    > [!NOTE]
    > 現在,您需要使用 Mage.exe 重新簽名檔。 有關詳細資訊,請參閱[演練:手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果從離線媒體(如 CD)安裝應用程式,並且電腦處於連線狀態,請[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]首先檢查部署清單中`<deploymentProvider>`標記指定的 URL,以確定更新位置是否包含應用程式的較新版本。 如果是,[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]請直接從那裡安裝應用程式,而不是從初始安裝目錄安裝應用程式,並且通用語言運行時 (CLR) 使用`<deploymentProvider>`確定應用程式的信任級別。 如果電腦處於離線狀態或`<deploymentProvider>`無法存取,則從[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]CD 進行安裝,CLR 會根據安裝點授予信任;否則,CLR 會根據安裝點授予信任。對於CD安裝,這意味著您的應用程式獲得完全信任。 所有後續更新都將繼承該信任級別。  
  
 使用[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]`<deploymentProvider>`的所有應用程式都應在其應用程式清單中顯式聲明所需的許可權,以便應用程式不會在不同的電腦上接收不同級別的信任。  
  
## <a name="see-also"></a>另請參閱  
 [演練:手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [單擊"一次性部署清單"](../deployment/clickonce-deployment-manifest.md)   
 [保護點選次數應用程式](../deployment/securing-clickonce-applications.md)   
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)
