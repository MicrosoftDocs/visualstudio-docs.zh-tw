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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414457"
---
# <a name="installing-the-visual-studio-sdk"></a>安裝 Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio 安裝的過程中安裝 Visual Studio SDK  
 如果您想要納入您的 Visual Studio 安裝的 VSSDK，您必須執行自訂安裝。  
  
> [!NOTE]
> 在安裝可執行檔，稱為 Visual Studio SDK **Visual Studio Extensibility Tools**。  
  
1. 啟動 Visual Studio 2015 安裝。 您可以安裝 Visual Studio Express 以外的任何版本。  
  
2. 在第一個畫面上，選取**自訂**，而非**預設**。 按 [ **下一步**]。  
  
3. 您應該會看到樹狀檢視的自訂功能。 開啟**常見工具**。 您應該會看到**Visual Studio Extensibility Tools** 。  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. 請檢查**Visual Studio Extensibility Tools** ，然後按一下**下一步**並繼續安裝。  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>安裝 Visual Studio 之後安裝 Visual Studio SDK  
 如果您決定要安裝 Visual Studio SDK，完成您的 Visual Studio 安裝之後，您應該遵循下列程序：  
  
1. 移至**控制台中 / 程式 / 程式和功能**，然後尋找**Visual Studio 2015**。 您可以安裝適用於 Visual Studio 2015 Express 以外的任何版本的 Visual Studio SDK。  
  
2. 以滑鼠右鍵按一下**Visual Studio 2015**，然後按一下**變更**。 您應該會看到 [安裝] 頁面。  
  
3. 遵循相同的程序，如**Visual Studio 安裝的過程中安裝 Visual Studio SDK**上方。  
  
4. 按一下  **Visual Studio Extensibility Tools**安裝 Visual Studio SDK 的連結。  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>從方案安裝 Visual Studio SDK  
 如果您使用的擴充性專案中開啟的方案，但是未先安裝的 VSSDK，將提示您的 [方案總管] 上方反白顯示的資訊列。 它看起來應該像下面這樣：  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>從命令列安裝 Visual Studio SDK  
 您也可以使用從命令列安裝的 VSSDK **/InstallSelectableItems**切換 Visual Studio 安裝程式。 如需有關使用使用安裝程式的命令列參數的詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio 2015](../install/install-visual-studio-2015.md)。  
  
 若要安裝的 VSSDK 以無訊息模式使用 Visual Studio 2015 Community 安裝程式的方法如下：  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 請注意，您必須使用符合您已安裝 Visual Studio 版本的 Visual Studio 安裝程式。 例如，如果您有在電腦上安裝的 Visual Studio Enterprise，您必須執行 Visual Studio Enterprise 安裝程式 (vs_enterprise.exe)。
