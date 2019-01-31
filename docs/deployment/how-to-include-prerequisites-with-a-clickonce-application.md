---
title: HOW TO：包含 ClickOnce 應用程式的必要條件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b83272cedce161ce9122d5877ab4afecca1b3ec
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998504"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>HOW TO：隨著 ClickOnce 應用程式納入必要條件
在您隨 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式散發必要條件軟體之前，必須先將這些必要條件的安裝程式套件下載到您的開發電腦。 當您發行應用程式並選擇 [從應用程式的相同位置下載必要條件] 時，如果安裝程式套件不在 [套件] 資料夾中，就會發生錯誤。  
  
> [!NOTE]
>  若要加入.NET Framework 的安裝程式套件，請參閱[適用於開發人員的.NET Framework 部署指南](/dotnet/framework/deployment/deployment-guide-for-developers)。  
  
##  <a name="Package"></a> 若要使用 Package.xml 新增安裝程式套件  
  
1. 在 [檔案總管] 中，開啟 [套件] 資料夾。  
  
    根據預設，在 32 位元系統上路徑為 *C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*，而在 64 位元系統上路徑為 *C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*。  
  
2. 開啟您要新增的必要條件資料夾，然後開啟安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本的語言資料夾 (例如，**en** 代表英文)。  
  
3. 在 [記事本] 中，開啟 *Package.xml* 檔案。  
  
4. 找出**名稱**包含的項目**http://go.microsoft.com/fwlink**，並複製 URL。 包括 **LinkID** 部分。  
  
   > [!NOTE]
   >  如果沒有**名稱**項目包含**http://go.microsoft.com/fwlink**，開啟**Product.xml**必要條件的根資料夾中的檔案，並找出**fwlink**字串。  
  
   > [!IMPORTANT]
   >  有些必要條件包含多個安裝程式套件 (例如，用於 32 位元或 64 位元系統)。 如果有多個 [Name] 元素包含 **fwlink**，則必須針對每一個元素重覆其餘步驟。  
  
5. 將 URL 貼上瀏覽器的網址列，然後在系統提示您執行或儲存時，選擇 [儲存]。  
  
    這個步驟會將安裝程式檔下載至您的電腦。  
  
6. 將檔案複製到必要條件的根資料夾。  
  
    例如，若是 Windows Installer 4.5 必要條件，則將檔案複製到 *\Packages\WindowsInstaller4_5* 資料夾。  
  
    現在您可以隨應用程式散發安裝程式套件。  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用 ClickOnce 應用程式安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)