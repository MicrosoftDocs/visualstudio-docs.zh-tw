---
title: HOW TO：包含 ClickOnce 應用程式的必要條件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc9ba407e91ddc8125d2836c8e2bb4329d5ad91f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945323"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>HOW TO：與 ClickOnce 應用程式一起納入必要軟體
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在您隨 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 應用程式散發必要條件軟體之前，必須先將這些必要條件的安裝程式套件下載到您的開發電腦。 當您發行應用程式，並選擇**從我的應用程式的相同位置下載必要條件**，會發生錯誤，如果安裝程式套件不在**封裝**資料夾。  
  
> [!NOTE]
>  若要加入.NET Framework 的安裝程式套件，請參閱[適用於開發人員的.NET Framework 部署指南](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx)。  
  
##  <a name="Package"></a> 若要使用 Package.xml 新增安裝程式套件  
  
1.  在 [檔案總管] 中，開啟 [套件] 資料夾。  
  
     根據預設，在 32 位元系統上路徑為 C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages，在 64 位元系統上路徑為 C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages。  
  
2.  開啟您要新增的必要條件資料夾，然後開啟安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 版本的語言資料夾 (例如，**en** 代表英文)。  
  
3.  在 [記事本] 中，開啟 **Package.xml** 檔案。  
  
4.  找出**名稱**包含的項目**http://go.microsoft.com/fwlink**，並複製 URL。 包括 **LinkID** 部分。  
  
    > [!NOTE]
    >  如果沒有**名稱**項目包含**http://go.microsoft.com/fwlink**，開啟**Product.xml**必要條件的根資料夾中的檔案，並找出**fwlink**字串。  
  
    > [!IMPORTANT]
    >  有些必要條件包含多個安裝程式套件 (例如，用於 32 位元或 64 位元系統)。 如果有多個 [Name] 元素包含 **fwlink**，則必須針對每一個元素重覆其餘步驟。  
  
5.  將 URL 貼上瀏覽器的網址列，然後在系統提示您執行或儲存時，選擇 [儲存]。  
  
     這個步驟會將安裝程式檔下載至您的電腦。  
  
6.  將檔案複製到必要條件的根資料夾。  
  
     例如，若是 Windows Installer 4.5 必要條件，則將檔案複製到 \Packages\WindowsInstaller4_5 資料夾。  
  
     現在您可以隨應用程式散發安裝程式套件。  
  
## <a name="see-also"></a>另請參閱  
 [如何：隨著 ClickOnce 應用程式安裝必要軟體](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
