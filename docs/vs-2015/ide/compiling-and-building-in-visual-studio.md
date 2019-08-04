---
title: 編譯和建置
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b534e46f4cdef87641207ec13419d4c59d04ed3f
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2019
ms.locfileid: "68740082"
---
# <a name="compiling-and-building-in-visual-studio"></a>在 Visual Studio 中編譯與建置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在開發週期期間，經常地使用 Visual Studio 來建置應用程式，並建立組件和可執行程式。 藉由經常建置程式碼，您可以更早識別編譯時期錯誤，例如錯誤的語法、拼錯的關鍵字和類型不相符。 您也可以藉由經常建置和執行程式碼的偵錯版本，偵測並修正執行階段錯誤，例如邏輯錯誤和語意錯誤。

 當您完整地開發並充分偵錯專案或方案時，就可以將其元件編譯在發行組建中。 根據預設，發行組建已最佳化，並設計成更小且執行速度比偵錯版本快。 如需詳細資訊，請參閱[逐步解說：建置應用程式](../ide/walkthrough-building-an-application.md)。

## <a name="choosing-a-build-method"></a>選擇建置方法
 您可以在 IDE 中使用預設組建選項、在命令提示字元，或使用 Team Foundation Build 來建置應用程式。 每個選項都使用 MSBuild 作為基礎的技術，且每一種方法都具有特定的優點，如下表所示。

|建置方法|權益|如需詳細資訊|
|------------------|--------------|--------------------------|
|使用 IDE|- 您可以更輕鬆地立即建立和執行組建。<br />- 您可以針對 C++ 和 C# 專案執行多處理器組建。<br />- 您可以自訂建置系統的某些層面。|[在 Visual Studio 中建置和清除專案與方案](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|執行 MSBuild 命令列|- 您可以建置專案，而不需要安裝 Visual Studio。<br />- 您可以針對所有專案類型執行多處理器組建。<br />- 您可以自訂大部分的建置系統。|[MSBuild](../msbuild/msbuild.md)|
|使用 Team Foundation Build|-  您可以自動化您的建置流程。 例如，您可以每晚或在每次簽入程式碼時建置一或多個專案。 您也可以在共用的組置伺服器上建置專案，而不是在開發電腦上建置。<br />- 您可以快速指定您想要建置的程式碼、想要執行的測試，和其他常見的選項。<br />- 您可以修改建置工作流程，並視需要建立建置活動執行深入自訂的工作。|[建置應用程式](/azure/devops/pipelines/index)|

## <a name="building-from-the-ide"></a>從 IDE 建置
 當您建立專案時，會定義它的預設組建組態，並指派方案組建組態給它以提供組建的內容。 方案組態會定義如何建立和部署方案中的專案。 專案組態是一組專案屬性，它們對於平台和組建類型 (例如，版本 Win32) 而言是唯一的。 您可以編輯這些預設組態，且可以建立自己的組態。 如需詳細資訊, 請參閱[專案設計](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)工具簡介[和操作說明:修改專案屬性和設定](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)。

 您可以從 IDE 中執行下列其他工作︰

- [變更組建輸出目錄](../ide/how-to-change-the-build-output-directory.md)。

- [識別出相依於另一個專案的輸出，才能正確建置的專案](../ide/how-to-create-and-remove-project-dependencies.md)。

- [變更組建記錄檔或組建輸出視窗中包含的資訊量](../ide/how-to-view-save-and-configure-build-log-files.md)。

- [隱藏 Visual C#、Visual C++ 或 Visual Basic 的特定編譯器警告](../ide/how-to-suppress-compiler-warnings.md)。

- [指定組建的自訂預先編譯和編譯後動作](../ide/specifying-custom-build-events-in-visual-studio.md)。

- 使用平行組建，以改善建置效能。 如需詳細資訊，請參閱[同時建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)或部落格文章 [Tuning C++ build parallelism](http://blogs.msdn.com/b/msbuild/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx) (調整 C++ 組建平行處理原則)。

## <a name="see-also"></a>另請參閱
 [逐步解說：建立應用程式](../ide/walkthrough-building-an-application.md) [瞭解組建](../ide/understanding-build-configurations.md)設定[瞭解組建平臺](../ide/understanding-build-platforms.md)[建立 (編譯) 網站專案](https://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [如何:建立及移除專案相依性](../ide/how-to-create-and-remove-project-dependencies.md)
