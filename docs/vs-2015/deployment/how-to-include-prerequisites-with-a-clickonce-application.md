---
title: 如何：在 ClickOnce 應用程式中包含必要條件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9639da1f735095f6d04a59d1f2302f822423e006
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557671"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>如何：將必要條件納入 ClickOnce 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在您隨 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式散發必要條件軟體之前，必須先將這些必要條件的安裝程式套件下載到您的開發電腦。 當您發行應用程式並選擇 **[從應用程式的相同位置下載必要條件**] 時，如果安裝程式套件不在 [ **封裝** ] 資料夾中，就會發生錯誤。  
  
> [!NOTE]
> 若要加入 .NET Framework 的安裝程式套件，請參閱 [.NET Framework 開發人員的部署指南](/dotnet/framework/deployment/deployment-guide-for-developers)。  
  
## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> 若要使用 Package.xml 新增安裝程式套件  
  
1. 在 [檔案總管] 中，開啟 [套件]**** 資料夾。  
  
     根據預設，在 32 位元系統上路徑為 C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages，在 64 位元系統上路徑為 C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages。  
  
2. 開啟您要新增的必要條件資料夾，然後開啟安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 版本的語言資料夾 (例如，**en** 代表英文)。  
  
3. 在 [記事本] 中，開啟 **Package.xml** 檔案。  
  
4. 找出包含的 **Name** 元素 `http://go.microsoft.com/fwlink` ，並複製 URL。 包括 **LinkID** 部分。  
  
    > [!NOTE]
    > 如果沒有 **名稱** 專案包含 `http://go.microsoft.com/fwlink` ，請在必要專案的根資料夾中開啟 **Product.xml** 檔案，並找出 **fwlink** 字串。  
  
    > [!IMPORTANT]
    > 有些必要條件包含多個安裝程式套件 (例如，用於 32 位元或 64 位元系統)。 如果有多個 [Name]**** 元素包含 **fwlink**，則必須針對每一個元素重覆其餘步驟。  
  
5. 將 URL 貼上瀏覽器的網址列，然後在系統提示您執行或儲存時，選擇 [儲存]****。  
  
     這個步驟會將安裝程式檔下載至您的電腦。  
  
6. 將檔案複製到必要條件的根資料夾。  
  
     例如，若是 Windows Installer 4.5 必要條件，則將檔案複製到 \Packages\WindowsInstaller4_5 資料夾。  
  
     現在您可以隨應用程式散發安裝程式套件。  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用 ClickOnce 應用程式安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
