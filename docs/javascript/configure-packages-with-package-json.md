---
title: 使用 package.json 設定 npm 套件
description: 使用 package.json 指定 npm 套件版本
ms.date: 09/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 891822d0b79cbfd53cf14229f11e003bf740c660
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969486"
---
# <a name="packagejson-configuration"></a>package.json 組態

如果您正在開發具有大量 npm 套件的 Node.js 應用程式，在您建置專案時，如果已更新一或多個套件，則遇到警告或錯誤的情況屢見不鮮。 有時候，版本會與結果衝突，或是套件版本已淘汰。 以下是一些快速提示，可協助您設定 [package.json](https://docs.npmjs.com/files/package.json) 檔案，並了解在您看到警告或錯誤時發生什麼情況。 這不是 *package.json* 的完整指南，而只著重於 npm 套件版本控制。

Npm 套件版本控制系統有嚴格的規則。 版本格式如下：

```
[major].[minor].[patch]
```

假設您的應用程式中有 5.2.1 版的套件。 主要版本是 5，次要版本是 2，而修補程式是 1。

* 在主要版本更新中，套件會包含回溯不相容的新功能，亦即重大變更。
* 在次要版本更新中，新功能已新增到與稍早套件版本回溯相容的套件。
* 在修補程式更新中，包含一或多個 Bug 修正。 Bug 修正一律會回溯相容。

值得注意的是，某些 npm 套件功能具有相依性。 比方說，若要使用 TypeScript 編譯器套件的新功能 (ts-loader) 搭配 webpack，可能您也需要更新 webpack npm 套件和 webpack-cli 套件。

為了協助管理套件版本控制，npm 支援數種標記法，您可以用於 *package.json*。 您可以使用這些標記法來控制想要在應用程式中接受的套件更新類型。

假設您使用 React，而且需要包含 **react** 和 **react-dom** npm 套件。 您可以在 *package.json* 檔案中用多種方式指定。 比方說，您可以指定使用套件的確切版本，如下所示。

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

使用上述的標記法，npm 一律會取得指定的確切版本，也就是 16.4.2。

您可以使用特殊標記法，來將更新限制為修補程式更新 (Bug 修正程式)。 在此範例中：

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

您可以使用波狀符號 (~) 字元，告知 npm 只在修補時更新套件。 因此，npm 可以將 react 16.4.2 更新至 16.4.3 (或 16.4.4 等等)，但它不會接受更新至主要或次要版本。 因此，16.4.2 不會更新至 16.5.0。

您也可以使用插入號 (^) 符號，指定 npm 可以更新次要版本號碼。

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

使用此標記法，npm 可以將 react 16.4.2 更新至 16.5.0 (或 16.5.1、16.6.0 等等)，但它不會接受更新至主要版本。 因此，16.4.2 不會更新至 17.0.0。

當 npm 更新套件時，它會產生 *package-lock.json* 檔案，其中列出您應用程式使用的實際 npm 套件版本，包括所有巢狀套件。 雖然 *package.json* 控制應用程式的直接相依性，但它不會控制巢狀相依性 (特定 npm 套件所需的其他 npm 套件)。 如果您需要確定其他開發人員和測試人員使用您正在使用的確切套件，包括巢狀套件，可以在開發週期中使用 *package-lock.json* 檔案。 如需詳細資訊，請參閱 npm 文件中的 [package-lock.json](https://docs.npmjs.com/files/package-lock.json)。

對 Visual Studio 而言，*package-lock.json* 檔案不會新增至您的專案，但您可以在專案資料夾中找到它。
