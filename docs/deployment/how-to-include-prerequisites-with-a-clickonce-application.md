---
title: 如何： 包含 ClickOnce 應用程式的必要條件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f961229e60cb291efdd7630f9df10e162c2f17b
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153838"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>如何： 包含 ClickOnce 應用程式的必要條件
在您隨 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式散發必要條件軟體之前，必須先將這些必要條件的安裝程式套件下載到您的開發電腦。 當您發行應用程式，並選擇**從我的應用程式的相同位置下載必要條件**，會發生錯誤，如果安裝程式套件不在**封裝**資料夾。  
  
> [!NOTE]
>  若要加入.NET Framework 的安裝程式套件，請參閱[適用於開發人員的.NET Framework 部署指南](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx)。  
  
##  <a name="Package"></a> 若要使用 Package.xml 加入安裝程式套件  
  
1.  在 [檔案總管] 中，開啟**封裝**資料夾。  
  
     根據預設，路徑是*C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* 32 位元系統上和*C:\Program Files (x86) \Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* 64 位元系統上。  
  
2.  開啟您要新增之必要條件的資料夾，然後開啟您已安裝的版本適用的語言資料夾[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)](例如**en**英文)。  
  
3.  在記事本中，開啟*Package.xml*檔案。  
  
4.  找出**名稱**包含的項目**http://go.microsoft.com/fwlink**，並複製 URL。 包含**LinkID**部分。  
  
    > [!NOTE]
    >  如果沒有**名稱**項目包含**http://go.microsoft.com/fwlink**，開啟**Product.xml**必要條件的根資料夾中的檔案，並找出**fwlink**字串。  
  
    > [!IMPORTANT]
    >  有些必要條件包含多個安裝程式套件 (例如，用於 32 位元或 64 位元系統)。 如果有多個**名稱**項目包含**fwlink**，您必須為每個重複的其餘步驟。  
  
5.  將 URL 貼到您的瀏覽器的網址列，然後提示您執行或儲存時，請選擇**儲存**。  
  
     這個步驟會將安裝程式檔下載至您的電腦。  
  
6.  將檔案複製到必要條件的根資料夾。  
  
     比方說，Windows Installer 4.5 必要條件，將檔案複製到*\Packages\WindowsInstaller4_5*資料夾。  
  
     現在您可以隨應用程式散發安裝程式套件。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 使用 ClickOnce 應用程式安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)