---
title: 將鍵盤快捷鍵綁定到功能表項 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94feafbc614be61aaa4eef9e26669c0fbe901ed5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740031"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>將鍵盤快捷鍵繫結到選單項目
要將鍵盤快捷方式綁定到自定義功能表命令,只需向包的 *.vsct*檔添加一個條目。 本主題介紹如何將鍵盤快捷方式映射到自定義按鈕、功能表項或工具列命令,以及如何在預設編輯器中應用鍵盤映射或將其限制為自定義編輯器。

 要將鍵盤快捷鍵分配給現有的 Visual Studio 選單項目,請參考[辨識與自訂鍵盤捷徑](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。

## <a name="choose-a-key-combination"></a>選擇鍵組合
 許多鍵盤快捷鍵已在可視化工作室中使用。 不應將同一快捷方式分配給多個命令,因為重複綁定很難檢測到,並且還可能導致不可預知的結果。 因此,最好在分配快捷方式之前驗證快捷方式的可用性。

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>驗證鍵盤快速鍵的可用性

1. 在 **「工具** > **」選項** > **環境「** 視窗中,選擇 **」鍵盤**」。

2. 使用**新快捷方式**設定為**全域**。

3. 在 **「按」鍵「** 框中,鍵入要使用的鍵盤快捷方式。

    如果快捷方式已在 Visual Studio 中使用,則「當前由」框**使用的快捷方式**將顯示快捷方式當前調用的命令。

4. 嘗試不同的鍵組合,直到找到未映射的鍵。

   > [!NOTE]
   > 使用**Alt**的鍵盤快捷鍵可能會打開功能表,而不是直接執行命令。 因此,當您鍵入包含**Alt**的快捷方式時,框**當前使用的快捷方式**可能為空。您可以透過關閉**選項對話**框然後按鍵來驗證快捷方式未開啟選單。

   以下過程假定您具有具有功能表命令的現有 VSPackage。 如果您需要說明,請查看[使用選單指令建立延伸](../extensibility/creating-an-extension-with-a-menu-command.md)。

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>將鍵盤快捷配置指令

1. 開啟套件的 *.vsct*檔案。

2. 如果不存在,`<KeyBindings>``<Commands>`則在之後創建空節。

   > [!WARNING]
   > 關於金鑰的資訊,請參考[金鑰的連結](../extensibility/keybinding-element.md)。

    在「`<KeyBindings>`部分」`<KeyBinding>`中, 創建一個條目。

    將`guid`和`id`屬性設置為要調用的命令的屬性。

    設定`mod1`屬性設定**為 「控制件****」、Alt**或**Shift**。

    "鍵綁定"部分應如下所示:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   如果鍵盤快捷鍵需要兩個以上鍵,請設置`mod2``key2`和 屬性。

   在大多數情況下,不應在沒有第二個修改器的情況下使用**Shift,** 因為按下它已會導致大多數字母數位鍵鍵入大寫字母或符號。

   虛擬金鑰代碼允許您存取沒有與其關聯的字元的特殊鍵,例如函數鍵和**Backspace**鍵。 有關詳細資訊,請參閱[虛擬金鑰碼](/windows/desktop/inputdev/virtual-key-codes)。

   要讓這個指令在 Visual Studio 編輯器`editor`中可用`guidVSStd97`, 將屬性設定為 。

   要使該命令僅在自訂編輯器中可用,可以將`editor`該屬性設置為創建包含自定義編輯器的 VSPackage 時[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]包範本生成的自訂編輯器的名稱。 要查找名稱`<Symbols>`值,請`<GuidSymbol>``name`查看 屬性以「`editorfactory`結尾的 節點的節。這是自定義編輯器的名稱。

## <a name="example"></a>範例
 本示例將鍵盤快捷鍵**Ctrl**+**Alt**+`cmdidMyCommand`**C**`MyPackage`綁定 到名為的包中命名的命令。

```
<CommandTable>
. . .
<Commands>
. . .
</Commands>
<KeyBindings>
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />
</KeyBindings>
. . .
</CommandTable>
```

## <a name="example"></a>範例
 本示例將鍵盤快捷鍵**Ctrl**+**B**`cmdidBold`繫`TestEditor`結定到 名為的專案中命名的命令。 該命令僅在自定義編輯器中可用,而在其他編輯器中不可用。

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>另請參閱
- [延伸選單與指令](../extensibility/extending-menus-and-commands.md)
