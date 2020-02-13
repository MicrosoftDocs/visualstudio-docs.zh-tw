---
title: DSL 的 VSIX 部署 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be9d3d44bfceaae1f2912086c3d20c90ce1e094b
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916553"
---
# <a name="vsix-deployment-of-a-dsl"></a>DSL 的 VSIX 部署
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在自己的電腦或其他電腦上安裝特定領域語言。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 必須已安裝在目的電腦上。

## <a name="Installing"></a>使用 VSX 安裝和卸載 DSL
 當您使用此方法安裝 DSL 時，使用者可以從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中開啟 DSL 檔案，但無法從 Windows Explorer 開啟該檔案。

#### <a name="to-install-a-dsl-by-using-the-vsix"></a>使用 VSIX 安裝 DSL

1. 在您的電腦中，尋找您的 DSL 封裝專案所建立的 **.vsix**檔案。

    1. 在**方案總管**中，以滑鼠右鍵按一下**DslPackage**專案，然後按一下 [**在 Windows Explorer 中開啟資料夾**]。

    2. 找出 **\*\\yourproject。的 bin\\** **。DslPackage .vsix**

2. 將 .vsix 檔案複製到您要安裝 DSL 的目的電腦 **。** 這可以是您自己的電腦或另一部電腦。

    - 目的電腦必須具有在執行時間支援 Dsl 的其中一個 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 版本。 如需詳細資訊，請參閱[支援的 Visual Studio 版本 & 模型 SDK 的視覺效果](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)。

    - 目的電腦必須具有**DslPackage\source.extensions.manifest**中指定的其中一個 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 版本。

3. 在目的電腦上，按兩下 **.vsix**檔案。

     [Visual Studio 擴充功能安裝程式] 隨即開啟並安裝擴充功能。

4. 啟動或重新啟動 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]。

5. 若要測試 DSL，請使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 建立新的檔案，該檔案具有您為 DSL 定義的副檔名。

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>卸載使用 VSX 安裝的 DSL

1. 在 [**工具**] 功能表上，按一下 [**擴充管理員**]。

2. 展開 [已安裝的擴充功能]。

3. 選取用來定義 DSL 的延伸模組，然後按一下 [**卸載**]。

   在很少見的情況下，錯誤的擴充功能會無法載入，並且在錯誤視窗中建立報表，但不會顯示在擴充管理員中。 在此情況下，您可以藉由從下列位置刪除檔案來移除擴充功能：

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**
