---
title: 其他檔案
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- builds [Visual Studio], miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], outside of containers
- files [Visual Studio], Miscellaneous Files folder
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2e00e836725620c9a3ded6e2df5119a66d1cb54
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942278"
---
# <a name="miscellaneous-files"></a>其他檔案
您可能想要使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 編輯器，單獨處理專案或方案中的檔案。 開啟方案時，可以開啟並修改檔案，而不需要將它們新增至方案或專案。 您想要單獨處理稱為其他檔案的容器中檔案。 其他檔案是方案和專案的外部檔案、未納入組建中，而且不能隨附於原始檔控制下的方案。

 單獨開啟容器中的檔案因各種原因而十分有用。 您可能有想要在開發專案方案時檢視但不是方案開發之必要項目的檔案。 常見範例包括開發附註或指示、資料庫結構描述和程式碼片段。 此外，您可能想要建立獨立檔案。

 ![方案專案](../../ide/reference/media/projects_solutions_misc.gif)

 如果啟用資料夾的選項，方案總管可以顯示檔案的 [其他檔案] 資料夾。 您可以從[選項對話方塊、環境、文件](../../ide/reference/documents-environment-options-dialog-box.md)設定選項。 關閉其他檔案之後，除非同時啟用該其他檔案的選項，否則不會與任何特定方案或專案建立關聯。

 [其他檔案] 資料夾會將檔案呈現為連結。 雖然此資料夾不是方案的一部分，但是開啟方案時，會重新開啟在最後一次關閉方案時開啟的部分或所有其他檔案 (視資料夾的設定而定)。

> [!NOTE]
> 未出現在 [其他檔案] 資料夾中的檔案有些是您無法在 IDE 內修改的檔案 (例如 .zip 檔案和 .doc 檔案)。 IDE 將不會追蹤只能透過外部編輯器修改的檔案。


## <a name="commands-available-in-the-ide"></a>IDE 中可用的命令
 功能表、工具列和其包含的命令會根據所開啟檔案的格式變更。 例如，開啟文字檔時，[文字編輯器] 工具列會出現，並且可以使用其命令。 如果您接著開啟 XML 結構描述檔案，則會出現 [XML 結構描述] 工具列。 編輯 XML 結構描述時，無法使用 [文字編輯器] 工具列的命令 (或工具列本身)。 XML 結構描述是使用中視窗，因而包含目前選取項目內容。 切換專案檔與其他檔案時，所有專案相關命令都會消失，只會出現與其他檔案直接相關的命令。

## <a name="folder-display-options"></a>資料夾顯示選項
 您可以設定 [其他資料夾] 的顯示選項，以顯示資料夾，即使您尚未開啟任何其他檔案也是一樣。 方案檔不會永久管理其他檔案的清單。 它會使用選擇性功能，以記住每位使用者最常使用 (MRU) 的檔案清單。

## <a name="see-also"></a>請參閱

- [專案和方案](../../ide/solutions-and-projects-in-visual-studio.md)
- [選項對話方塊、環境、文件](../../ide/reference/documents-environment-options-dialog-box.md)