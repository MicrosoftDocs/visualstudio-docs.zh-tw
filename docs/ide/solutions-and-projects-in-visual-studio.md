---
title: "Visual Studio 中的方案和專案 | Microsoft Docs"
ms.custom: 
ms.date: 10/5/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.newproject
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- projects [Visual Studio], setting up
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca3094b3bfe35381236798164fa18e58304bae3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio 中的方案和專案
當您在 Visual Studio 中建立 App、網站、外掛程式等項目時，您必須開始一個「專案」。 在邏輯方面而言，專案包含所有原始程式碼檔案、圖示、影像、資料檔案以及其他會編譯到可執行程式或網站的項目，或是執行編譯所需的項目。 專案也包含所有編譯器設定與其他組態檔，這些是您的程式將與其通訊的各種服務或元件所需的項目。  

> [!NOTE]
>  如果您不想要，則不需要使用方案或專案。 您只需要在 Visual Studio 中開啟檔案，並開始編輯程式碼。 如需詳細資訊，請參閱[在 Visual Studio 中不使用專案或方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。  

專案 (.vbproj、.csproj、.vcxproj) 是 XML 檔案，它定義虛擬資料夾階層，以及專案中所有項目的路徑。 它也包含組建設定。 若要查看專案檔的內容，您可以在方案總管中選取專案名稱，然後從內容 (以滑鼠右鍵按一下) 功能表選擇 [卸載專案]。 然後，再次開啟內容功能表並選擇 [編輯 \<專案名稱\>]。  

在 Visual Studio 中，[方案總管] 會使用專案檔來顯示專案內容與設定。 當您編譯專案時，MSBuild 引擎會使用專案檔來建立可執行檔。 您也可以自訂專案來產生其他類型的輸出。  

就邏輯與檔案系統方面而言，專案是包含在「解決方案」內，這可能包含一或多個相關專案，以及建置資訊、Visual Studio 視窗設定與任何未與特定專案建立關聯的其他檔案。 解決方案由具有自己獨特格式的文字檔 (.sln) 所描述；它通常不適合手動編輯。  

方案具有關聯的 *.suo* 檔案，其中儲存每個專案使用者的設定、喜好設定與組態資訊。  

 下圖顯示專案與方案和其邏輯上包含之項目之間的關係。  

 ![Visual Studio 專案及方案](../ide/media/vside-project-diagram.png)  

## <a name="creating-new-projects"></a>建立新專案  
 建立新專案最簡單的方式是從專案範本開始，它們是由預先產生的程式碼檔案、組態檔、資產與設定的基本集合所組成，可讓您開始以特定的程式設計語言來建立特定類型的應用程式或網站。 這些範本是當您選擇 [檔案]、[新增]、[專案] 或 [檔案]、[新增]、[網站] 時，在 [新增專案] 或 [新增網站] 對話方塊中看到的內容。 如需詳細資訊，請參閱[建立方案與專案](../ide/creating-solutions-and-projects.md)。  

您也可以建立自訂專案與項目範本。 如需詳細資訊，請參閱[建立專案和項目範本](../ide/creating-project-and-item-templates.md)。  

## <a name="managing-projects-in-solution-explorer"></a>管理 [方案總管] 中的專案  
 建立新專案之後，您可以使用 [方案總管]  來檢視及管理專案與方案，以及關聯的項目。 下圖顯示方案總管與包含兩個專案的 C# 方案。  

 ![方案總管](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>本章節內容  

-   [建立解決方案和專案](../ide/creating-solutions-and-projects.md)  

-   [新增和移除專案項目](../ide/adding-and-removing-project-items.md)  

-   [管理專案和解決方案屬性](../ide/managing-project-and-solution-properties.md)  

-   [管理專案中的參考](../ide/managing-references-in-a-project.md)  

-   [應用程式屬性](../ide/application-properties.md)  

-   [管理組件和資訊清單簽署](../ide/managing-assembly-and-manifest-signing.md)  

-   [如何：指定應用程式圖示 (Visual Basic、C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [以特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [建立專案和項目範本](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>另請參閱  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
