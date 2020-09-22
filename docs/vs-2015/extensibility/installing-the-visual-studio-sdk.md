---
title: 安裝 Visual Studio SDK |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88a6266a3f5910def0bf5041a37f89c2b3d67416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840255"
---
# <a name="installing-the-visual-studio-sdk"></a>安裝 Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>在 Visual Studio 安裝過程中安裝 Visual Studio SDK  
 如果您想要在 Visual Studio 安裝中包含 VSSDK，您必須進行自訂安裝。  
  
> [!NOTE]
> 在安裝可執行檔中，Visual Studio SDK 稱為 **Visual Studio 擴充性工具**。  
  
1. 啟動 Visual Studio 2015 安裝。 您可以安裝任何版本的 Visual Studio （Express 除外）。  
  
2. 在第一個畫面上，選取 [ **自訂**]，而非 [ **預設**]。 按一下 [下一步]。  
  
3. 您應該會看到自訂功能的樹狀檢視。 開啟 [ **一般工具**]。 您應該會看到 **Visual Studio 擴充性工具** 。  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. 檢查 **Visual Studio 擴充性工具** ，然後按 **[下一步]** 繼續安裝。  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>在安裝 Visual Studio 之後安裝 Visual Studio SDK  
 如果您決定在完成 Visual Studio 安裝之後安裝 Visual Studio SDK，您應該遵循下列程式：  
  
1. 移至 **主控台/程式/程式和功能**，並尋找 **Visual Studio 2015**。 您可以安裝 Visual Studio SDK，適用于任何版本的 Visual Studio 2015 （Express 除外）。  
  
2. 在 [ **Visual Studio 2015**] 上按一下滑鼠右鍵，然後按一下 [ **變更**]。 您應該會看到 [安裝] 頁面。  
  
3. 遵循與 **安裝 VISUAL STUDIO SDK** 的相同程式，做為上述 Visual Studio 安裝的一部分。  
  
4. 按一下 **Visual Studio 擴充性工具** 連結，以安裝 Visual Studio SDK。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>從解決方案安裝 Visual Studio SDK  
 如果您在沒有先安裝 VSSDK 的情況下開啟具有擴充性專案的方案，則會在方案總管上方以醒目提示的資訊列提示您。 您應該會看到如下的內容：  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>從命令列安裝 Visual Studio SDK  
 您可以使用 **/InstallSelectableItems** 參數搭配 Visual Studio 安裝程式，從命令列安裝 VSSDK。 如需搭配安裝程式使用命令列參數的詳細資訊，請參閱 [安裝 Visual Studio 2015](../install/install-visual-studio-2015.md)。  
  
 以下是如何使用 Visual Studio 2015 社區安裝程式以無訊息方式安裝 VSSDK：  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 請注意，您必須使用符合已安裝之 Visual Studio 版本的 Visual Studio 安裝程式。 例如，如果您的電腦上已安裝 Visual Studio Enterprise，則必須執行 Visual Studio Enterprise 安裝程式 ( # A0) 。
