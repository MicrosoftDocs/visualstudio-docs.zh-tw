---
title: 了解組建組態
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb699b02723e88454f26f4b897cfd7ba3ff46592
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32425121"
---
# <a name="understand-build-configurations"></a>了解組建組態

您可以儲存不同的方案和專案屬性組態，以用於不同類型的組建。 若要建立、選取、修改或刪除組態，您可以使用 [組態管理員]。 若要開啟組態，請在功能表列上，選擇 [建置] > [組態管理員]，或直接在 [快速啟動] 方塊中鍵入**組態**。 您也可以使用 [標準] 工具列上的 [方案組態] 清單，來選取組態或開啟 [組態管理員]。

> [!NOTE]
> 如果您在工具列上找不到方案組態設定，而且無法存取 [組態管理員]，則可能會套用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 開發設定。 如需詳細資訊，請參閱[如何：在套用 Visual Basic 開發者設定的情況下管理組態](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md)。

根據預設，使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 範本所建立的專案會包含偵錯和發行組態。 偵錯組態支援應用程式的偵錯，而發行組態則會建置可部署的應用程式版本。 如需詳細資訊，請參閱[如何：設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)。 您也可以建立自訂方案組態和專案組態。 如需詳細資訊，請參閱[如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)。

## <a name="solution-configurations"></a>方案組態

方案組態指定如何建置和部署方案中的專案。 若要修改方案組態或定義新的組態，請在 [組態管理員] 的 [使用中的方案組態] 下，選擇 [編輯] 或 [新增]。

方案組態之 [專案內容] 方塊中的每個項目，分別代表方案中的一個專案。 針對 [使用中的方案組態] 和 [使用中的方案平台] 的每種組合，您可以設定每個專案的使用方式 (如需方案平台的詳細資訊，請參閱[了解組建平台](../ide/understanding-build-platforms.md))。

> [!NOTE]
> 當您定義新的方案組態並選取 [建立新專案組態] 核取方塊時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會將新的組態自動指派給所有專案。 同樣地，當您定義新的方案平台並選取 [建立新專案組態] 核取方塊時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會將新的平台自動指派給所有專案。 此外，如果您加入以新平台為目標的專案，Visual Studio 會將該平台加入方案平台清單中，並指派給所有專案。
>
> 您仍然可以修改每個專案的設定。

使用中的方案組態也會提供 IDE 的內容。 例如，如果您正在處理某個專案，且組態指定這個專案是針對行動裝置所建置，則 [工具箱] 只會顯示可用於行動裝置專案中的項目。

## <a name="project-configurations"></a>專案組態
 專案的目標組態和平台會一起用來指定建置時所要使用的屬性。 一個專案針對每種組態和平台組合，可以有一組不同的屬性定義。 若要修改專案的屬性，您可以使用其屬性頁。 (在方案總管中，開啟專案的捷徑功能表，然後選擇 [屬性])。

 您可以視需要針對每個專案組態，定義與組態相依的屬性。 例如，針對特定組建，您可以設定要包含的專案項目、要建立的輸出檔，要放置檔案的位置，以及最佳化檔案的方式。

 專案組態可能會有很大的差異。 例如，某個組態的屬性可能會指定將其輸出檔最佳化為佔用最小空間，而另一個組態則可能會指定其可執行檔以最高速度執行。

 專案組態是由方案 (而不是由使用者) 來儲存，以便小組可以共用這些組態。

 雖然專案相依性與組態無關，但是只會建置使用中方案組態中所指定的專案。

## <a name="how-visual-studio-assigns-project-configurations"></a>Visual Studio 如何指派專案組態
 當您定義新的方案組態，而不是從現有的組態複製設定時，Visual Studio 會使用下列準則來指派預設的專案組態。 準則的評估順序如下所示。

1.  如果專案具有完全符合新方案組態名稱的組態名稱 (*\<組態名稱> \<平台名稱>*)，則會指派該組態。 組態名稱不區分大小寫。

2.  如果專案組態名稱的組態名稱部分符合新的方案組態，則無論平台部分是否相符，都會指派該組態。

3.  如果仍然沒有相符項目，就會指派專案中所列的第一個組態。

## <a name="how-visual-studio-assigns-solution-configurations"></a>Visual Studio 如何指派方案組態
 當您建立專案組態 (透過在 [組態管理員] 中，選擇該專案 [組態] 欄之下拉式功能表中的 [新增]) 並選取 [建立新方案組態] 核取方塊時，Visual Studio 會尋找名稱相同的方案組態，以在每個支援的平台上建置專案。 在某些情況下，Visual Studio 會重新命名現有的方案組態，或定義新的組態。

 Visual Studio 使用下列準則來指派方案組態。

-   如果專案組態不會指定平台，或只指定一個平台，則會找到或加入其名稱符合新專案組態名稱的方案組態。 這個方案組態的預設名稱不包含平台名稱，其採用 *\<專案組態名稱>* 格式。

-   如果專案支援多個平台，則會為每個支援的平台找到或加入一個方案組態。 每個方案組態的名稱包含專案組態名稱和平台名稱，並且採用 *\<專案組態名稱> \<平台名稱>* 格式。

## <a name="see-also"></a>另請參閱

- [逐步解說：建置應用程式](../ide/walkthrough-building-an-application.md)
- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
- [方案和專案](../ide/solutions-and-projects-in-visual-studio.md)
- [C/C++ 組建參考](/cpp/build/reference/c-cpp-building-reference)
- [Devenv 命令列參數](../ide/reference/devenv-command-line-switches.md)