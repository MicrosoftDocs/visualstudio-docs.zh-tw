---
title: JavaScript、檔案屬性 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.expandedsdknode.fileversion
- javascript.project.property.expandedsdknode.uri
- javascript.project.property.expandedsdknode.filename
- javascript.project.property.reference.description
- javascript.project.property.reference.specificversion
- javascript.project.property.reference.identity
- javascript.project.property.fullpath
- javascript.project.property.packageaction
- javascript.project.property.reference.package
- javascript.project.property.copytooutputdirectory
- javascript.project.property.expandedsdknode.sdkpath
- javascript.project.property.reference.filetype
- javascript.project.property.reference.culture
- javascript.project.property.filename
- javascript.project.property.reference.resolvedpath
- javascript.project.property.reference.version
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 719a956558141684c7d755aafb6929f4368482f7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657715"
---
# <a name="file-properties-javascript"></a>JavaScript、檔案屬性
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您可以使用檔案屬性，指出專案系統應該對檔案執行哪些動作。 例如，您可以設定檔案屬性，指出是否應該將檔案新增至套件以作為資源檔。

 您可以在方案總管中選取任何檔案，然後在 [屬性] 視窗中檢查其屬性。 JavaScript 檔案有四個屬性：[複製到輸出目錄]、[套件動作]、[檔案名稱] 和 [檔案路徑]。

## <a name="file-properties"></a>檔案內容
 此區段描述 JavaScript 檔案的共用屬性。

### <a name="copy-to-output-directory-property"></a>複製到輸出目錄屬性
 此屬性指定將選取的來源檔案複製到輸出目錄的條件。 如果永遠不要將檔案複製到輸出目錄，請選取 [不要複製]。 如果一律要將檔案複製到輸出目錄，請選取 [一律複製]。 只要複製版本比輸出目錄中同名現有檔案還要新的檔案時，請選取 [有更新時才複製]。

### <a name="package-action"></a>套件動作
 [套件動作] 屬性指出 Visual Studio 在執行組建時對檔案執行的動作。 [套件動作] 可以有數個值之一：

- **無**：檔案未包含在套件資訊清單中。 範例是包含讀我檔案這類文件的文字檔。

- **內容**：檔案包含在套件資訊清單中。 例如，此設定是 .htm、.js、.css、影像、音訊或視訊檔案的預設值。

- **資訊清單**：檔案未包含在套件資訊清單中。 相反地，產生套件資訊清單時，檔案是用於輸入。 這是 package.appxmanifest 檔案的預設值。

- **資源**：檔案未包含在套件資訊清單中。 相反地，會以進入套件資訊清單的套件資源索引 (PRI) 編製檔案內容的索引。 這通常用於資源檔。

  [套件動作] 的預設值取決於您新增至方案之檔案的副檔名。

### <a name="file-name-property"></a>檔案名稱屬性
 將檔案名稱顯示為唯讀值。 若要將檔案重新命名，您必須以滑鼠右鍵按一下方案總管，然後選取 [重新命名]。

### <a name="full-path-property"></a>完整路徑屬性
 將檔案的完整路徑顯示為唯讀值。 若要變更檔案的路徑，您可以在方案總管中拖放檔案。

## <a name="reference-file-properties"></a>參考檔案屬性
 此區段描述從 [!INCLUDE[win8_app_js](../../includes/win8-app-js-md.md)] 參考之檔案的共用屬性。 當您在方案總管中選取 .winmd 檔案這類參考、SDK 參考、專案對專案參考或組件參考時，根據檔案類型，可能會在 [屬性] 視窗中顯示其他屬性。

### <a name="culture"></a>culture
 顯示與參考建立關聯的語言。

### <a name="file-type"></a>檔案類型
 顯示參考的檔案類型。

### <a name="file-version"></a>檔案版本
 顯示參考的檔案版本。

### <a name="identity"></a>識別
 顯示專案中所使用參考的身分識別，這儲存在專案檔中。

### <a name="package"></a>封裝
 顯示與參考建立關聯的套件資訊清單名稱。

### <a name="resolved-path"></a>已解析路徑
 顯示專案中所使用參考的路徑。

### <a name="sdk-path"></a>SDK 路徑
 顯示所參考 SDK 檔案的路徑。

### <a name="uri"></a>URI
 顯示必須包含在專案 HTML 或 JavaScript 檔案中的 URI，以將檔案包含為來源檔案。

### <a name="version"></a>版本
 顯示參考的版本。

## <a name="see-also"></a>請參閱
 [筆尖：專案屬性（Visual Studio）](https://msdn.microsoft.com/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)
