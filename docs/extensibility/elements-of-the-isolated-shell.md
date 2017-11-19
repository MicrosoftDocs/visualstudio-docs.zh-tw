---
redirect_url: shell/elements-of-the-isolated-shell
title: "Isolated Shell 的項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15c32ccd3634529c63eb95eb698c3239b6c0e37e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="elements-of-the-isolated-shell"></a>Isolated Shell 的項目
您可以修改登錄設定、 執行階段設定和應用程式進入點，獨立的 shell 應用程式時，其.vsct、.pkgdef、 and.pkgundef 檔案。  
  
## <a name="registry-settings"></a>登錄設定  
 .pkgdef 和.pkgundef 檔案修改 isolated 的 shell 應用程式的登錄設定。 當應用程式執行時，依照以下順序定義登錄設定：  
  
 當應用程式執行時，依照以下順序定義登錄設定：  
  
1.  建立應用程式的登錄機碼。  
  
2.  從應用程式的.pkgdef 檔案會更新登錄，藉由定義指定之索引鍵和項目。  
  
3.  對於屬於您的應用程式的每個套件，.pkgdef 檔案，該封裝的更新登錄。 每個封裝中的應用程式的.pkgdef 檔定義 $RootKey$ \Packages\\{*vsPackageGuid*} 金鑰封裝。  
  
4.  從 AppEnvConfig.pkgdef 和 BaseConfig.pkgdef 中的更新登錄*Visual Studio SDK 安裝路徑*\Common7\IDE\ShellExtensions\Platform 目錄。 這些檔案是組件的 Visual Studio 以及 Visual Studio Shell （獨立的模式） 可轉散發套件的一部分。  
  
5.  從應用程式的.pkgundef 檔案會更新登錄，藉由移除指定的索引鍵和項目。  
  
## <a name="run-time-settings"></a>執行階段設定  
 當使用者開始獨立的 shell 應用程式時，它會呼叫在 Visual Studio shell 項目起點。 應用程式設定會定義您的應用程式啟動時，，如下所示：  
  
1.  Visual Studio shell 會檢查特定索引鍵的應用程式登錄。 如果開始進入點的呼叫中指定的索引鍵的設定，則該值會覆寫登錄中的值。  
  
2.  如果登錄都進入點參數指定之值的設定，則會使用預設值，此設定。  
  
 當使用者從命令列啟動您的應用程式時，所有的命令列參數會傳遞至 Visual Studio shell，將它們視為相同的方式，來 Devenv 中。 如需 Devenv 參數的詳細資訊，請參閱[Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)和[Devenv 命令列參數為 VSPackage 開發](../extensibility/devenv-command-line-switches-for-vspackage-development.md)。 如需封裝的命令列參數的暫存器的詳細資訊，請參閱[加入命令列參數](../extensibility/adding-command-line-switches.md)。  
  
## <a name="the-start-entry-point"></a>開始進入點  
 Appenvstub.dll 檔案包含用於存取在 isolated 的 shell 的進入點。 當應用程式啟動時，它會呼叫開始項目點的 Appenvstub.dll。  
  
 您可以變更應用程式的行為變更會傳遞至開始進入點的最後一個參數的值。 如需詳細資訊，請參閱[隔離 Shell 進入點參數 （c + +）](../extensibility/isolated-shell-entry-point-parameters-cpp.md)。  
  
## <a name="the-vsct-file"></a>。Vsct 檔案  
 .Vsct 檔可讓您指定應用程式中可用的標準 Visual Studio UI 項目。 如需詳細資訊，請參閱[。Vsct 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md)。  
  
## <a name="the-pkgundef-file"></a>。Pkgundef 檔案  
 在其已安裝 Visual Studio 的電腦上安裝應用程式時，應用程式建立的副本，Visual Studio 的登錄項目。 根據預設，應用程式會使用已安裝在電腦的 Vspackage。 .Pkgundef 檔案可讓您排除登錄項目以移除應用程式的 Visual Studio shell 或延伸模組的特定項目。 如需詳細資訊，請參閱[。Pkgundef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)。  
  
 .Pkgundef 檔案可讓您排除登錄項目以移除應用程式的 Visual Studio shell 或延伸模組的特定項目。 如需詳細資訊，請參閱[。Pkgundef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)。  
  
 中所列封裝 Guid，您可以排除一組[封裝 Guid 的 Visual Studio 功能](../extensibility/package-guids-of-visual-studio-features.md)。  
  
## <a name="the-pkgdef-file"></a>。Pkgdef 檔案  
 .Pkgdef 檔可讓您定義在安裝應用程式時所設定的應用程式的登錄項目。 .Pkgdef 檔的描述及使用 Visual Studio shell 的登錄項目清單，請參閱[。Pkgdef 檔案](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)。  
  
## <a name="substitution-strings"></a>替代字串  
 中所列的.pkgdef 和.pkgundef 檔案中使用的替代字串[中使用的替代字串。Pkgdef 和。Pkgundef 檔案](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)。  
  
## <a name="other-settings"></a>其他設定  
 如果您的獨立的 shell 應用程式相依於 Microsoft.VisualStudio.GraphModel.dll，您需要 Isolated Shell 應用程式的.config 檔案中加入下列繫結重新導向：  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```