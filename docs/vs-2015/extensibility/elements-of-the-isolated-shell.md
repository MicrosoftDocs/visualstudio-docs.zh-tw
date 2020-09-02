---
title: 隔離式 Shell 的元素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a95b7da718f050357f6ecd79c90c389dd6085d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204607"
---
# <a name="elements-of-the-isolated-shell"></a>獨立模式 Shell 的元素
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以修改登錄設定、執行時間設定，以及獨立 shell 應用程式的應用程式進入點，以及其 .vsct、. .pkgdef 和 .pkgundef 檔案。  
  
## <a name="registry-settings"></a>登錄設定  
 .Pkgdef 和 .pkgundef 檔案都會修改獨立 shell 應用程式的登錄設定。 當應用程式執行時，系統會以下列順序定義登錄設定：  
  
 當應用程式執行時，系統會以下列順序定義登錄設定：  
  
1. 建立應用程式的登錄機碼。  
  
2. 藉由定義指定的索引鍵和專案，從應用程式的 .pkgdef 檔案更新登錄。  
  
3. 針對屬於應用程式一部分的每個封裝，會從該套件的 .pkgdef 檔案更新登錄。 每個套件都是在應用程式的 .pkgdef 檔案中定義，由封裝的 $RootKey $ \Packages \\ {*vsPackageGuid*} 機碼來定義。  
  
4. 系統會在 *VISUAL STUDIO SDK 安裝路徑*\Common7\IDE\ShellExtensions\Platform 目錄中，從 AppEnvConfig. .Pkgdef 和 BaseConfig. .pkgdef 更新登錄。 這些檔案是 Visual Studio 的一部分，也是 Visual Studio Shell (獨立模式) 可轉散發套件的一部分。  
  
5. 藉由移除指定的索引鍵和專案，從應用程式的 .pkgundef 檔案更新登錄。  
  
## <a name="run-time-settings"></a>執行時間設定  
 當使用者啟動隔離式 shell 應用程式時，它會呼叫 Visual Studio shell 的開始進入點。 應用程式設定會在應用程式啟動時定義，如下所示：  
  
1. Visual Studio shell 會檢查應用程式登錄中的特定索引鍵。 如果在對開始進入點的呼叫中指定索引鍵的設定，則該值會覆寫登錄中的值。  
  
2. 如果登錄或進入點參數都沒有指定設定的值，則會使用設定的預設值。  
  
   當使用者從命令列啟動您的應用程式時，所有命令列參數都會傳遞至 Visual Studio shell，其會以 Devenv 的相同方式來處理它們。 如需 Devenv 參數的詳細資訊，請參閱 VSPackage 開發的 [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md) 和 [Devenv 命令列參數](../extensibility/devenv-command-line-switches-for-vspackage-development.md)。 如需封裝如何註冊命令列參數的詳細資訊，請參閱 [新增命令列參數](../extensibility/adding-command-line-switches.md)。  
  
## <a name="the-start-entry-point"></a>開始進入點  
 Appenvstub.dll 檔案包含用來存取隔離式 shell 的進入點。 當應用程式啟動時，它會呼叫 Appenvstub.dll 的開始進入點。  
  
 您可以藉由變更傳遞至開始進入點之最後一個參數的值，來變更應用程式的行為。 如需詳細資訊，請參閱 [ (c + +) 的獨立 Shell 進入點參數 ](../extensibility/isolated-shell-entry-point-parameters-cpp.md)。  
  
## <a name="the-vsct-file"></a>，..Vsct 檔案  
 .Vsct 檔案可讓您指定應用程式中可用的標準 Visual Studio UI 元素。 如需詳細資訊，請參閱 [。.Vsct](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md)檔案。  
  
## <a name="the-pkgundef-file"></a>，..Pkgundef 檔案  
 當應用程式安裝在已安裝 Visual Studio 的電腦上時，會為應用程式進行 Visual Studio 登錄專案的複本。 根據預設，應用程式會使用已安裝在電腦上的 Vspackage。 .Pkgundef 檔案可讓您排除登錄專案，以便從應用程式移除 Visual Studio shell 或延伸模組的特定元素。 如需詳細資訊，請參閱 [。.Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)檔案。  
  
 .Pkgundef 檔案可讓您排除登錄專案，以便從應用程式移除 Visual Studio shell 或延伸模組的特定元素。 如需詳細資訊，請參閱 [。.Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)檔案。  
  
 您可以排除的封裝 Guid 集合會列在 [Visual Studio 功能的封裝 guid](../extensibility/package-guids-of-visual-studio-features.md)中。  
  
## <a name="the-pkgdef-file"></a>，..Pkgdef 檔案  
 .Pkgdef 檔案可讓您定義安裝應用程式時所設定之應用程式的登錄專案。 如需 .pkgdef 檔案的描述以及 Visual Studio shell 使用的登錄專案清單，請參閱 [。.Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)檔案。  
  
## <a name="substitution-strings"></a>替代字串  
 .Pkgdef 和. .pkgundef 檔案中使用的替代字串會列在 [中使用的替代字串。.Pkgdef 和。.Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)檔案。  
  
## <a name="other-settings"></a>其他設定  
 如果您的隔離式 shell 應用程式相依于 Microsoft.VisualStudio.GraphModel.dll，您必須將下列系結重新導向新增至隔離式 Shell 應用程式的 .config 檔案：  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
