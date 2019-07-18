---
title: 錯誤：Windows 檔案共用已設定...|Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89224dc5394f248ea82d428731ef387cb705ff27
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850043"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>錯誤：Windows 檔案共用已設定...
已設定 Windows 檔案共用，這樣您將使用不同的使用者名稱連接到遠端電腦。 這與遠端偵錯不相容

 目前的檔案共用組態已設定為使用不同的使用者名稱連接到遠端電腦。 在此案例中無法使用遠端偵錯。

 若要更正這個問題，請使用其他帳戶名稱登入電腦，或變更檔案共用以使用您偵錯時所使用的帳戶名稱。

 如果要使用這個使用者名稱連接到遠端電腦，您必須先中斷連接遠端電腦。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 使用其他帳戶名稱登入您所進行偵錯的本機電腦 (Local Machine)。

     -或-

     。 中斷與遠端電腦的連線，然後將檔案共用重新設定成使用您的帳戶名稱連接至另一台電腦：

    1. 在 [開始] 功能表中，指向 [附屬應用程式]，然後按一下 [命令提示字元]。

    2. 在 Windows 命令提示字元中輸入：

         `net use /delete computer_name`

    3. 使用 Windows 說明中記載的任何方法，變更您的檔案共用設定。