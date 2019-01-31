---
title: 連接字串包含具有純文字密碼的認證，並且不使用整合式安全性
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 37155efecd7019c0de82d37ee8b071a74a29eea6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966526"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>連接字串包含具有純文字密碼的認證，並且不使用整合式安全性

是否要將連接字串連同這些敏感資訊一起儲存到目前的 DBML 檔案和應用程式組態檔？  按 [否] 只會儲存連接字串，而不會儲存敏感性資訊。

使用內含敏感資訊 (含在連接字串中的密碼) 的資料連接時，可以選擇是否在將連接字串儲存至專案的 DBML 檔案和應用程式組態檔時包含敏感資訊。

> [!WARNING]
> 將 [連線] 屬性的 [應用程式設定] 屬性明確設定為 [False]，會將密碼新增到 DBML 檔案中。

## <a name="save-options"></a>儲存選項

- 若要儲存的連接字串連同敏感資訊，請選擇**是**。

   連接字串會儲存為應用程式設定。 連接字串會包含純文字的敏感資訊。 DBML 檔案不包含敏感資訊。

- 若要儲存連接字串，不機密的資訊，請選擇**No**。

   連接字串會儲存為應用程式設定，但是不包含密碼。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)