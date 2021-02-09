---
title: 如何：以編碼方式儲存及開啟檔案
description: 瞭解如何以特定的編碼方式儲存及開啟檔案，因此當您開啟檔案時，Visual Studio 會正確地顯示檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d19b6f8e2e614ed397dee2e75807ded895a82d81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927908"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>如何：以編碼方式儲存及開啟檔案

您可以使用特定的字元編碼來儲存檔案，以支援雙向語言。 您也可以在開啟檔案時指定編碼方式，讓 Visual Studio 正確顯示檔案。

## <a name="to-save-a-file-with-encoding"></a>以編碼方式儲存檔案

1. 從 [檔案] 功能表上，選擇 [另存新檔]，然後按一下 [儲存] 按鈕旁的下拉式按鈕。

     [**進階儲存選項**] 對話方塊隨即出現。

2. 在 [編碼] 下方，選取檔案要使用的編碼方式。

3. 您也可以在 [行尾結束符號] 下方，選取行結尾字元的格式。

     如果您想要與不同作業系統的使用者交換檔案，這個選項相當實用。

     如果您知道要使用的檔案是以何種方式編碼，即可在開啟檔案時告知 Visual Studio 使用該種編碼方式。 依據檔案是否為專案的一部分而定，您需使用不同的方法。

> [!NOTE]
> 如果您想要以編碼方式儲存專案檔，則在卸載專案之前，不會啟用 [ **另存** 新檔] 選項。

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>若要開啟的編碼檔案為專案的一部分

1. 在方案總管中，以滑鼠右鍵按一下檔案，並選擇 [開啟方式]。

2. 在 [開啟方式] 對話方塊中，選擇要開啟檔案的編輯器。

     許多 Visual Studio 編輯器 (例如表單編輯器) 會自動偵測編碼，並以適當方式開啟檔案。 如果您選擇的編輯器可讓您選擇編碼方式，即會顯示 [編碼] 對話方塊。

3. 在 [編碼] 對話方塊中，選取編輯器應該使用的編碼方式。

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>若要開啟的編碼檔案不是專案的一部分

1. 在 [檔案] 功能表上，指向 [開啟]，並選擇 [檔案] 或 [從 Web 開啟檔案]，然後選取要開啟的檔案。

2. 按一下 [開啟] 按鈕旁的下拉式按鈕，然後選擇 [開啟方式]。

3. 遵循上述程序步驟 2 和 3。

## <a name="see-also"></a>另請參閱

- [編碼與分行符號](encodings-and-line-breaks.md)
- [編碼方式和 Windows Forms 全球化](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)
