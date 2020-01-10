---
title: 將鍵盤快速鍵系結至功能表項目 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98c0b6f5b26e7f423f2a89f680395ceaba7286bc
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982278"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>將鍵盤快速鍵系結至功能表項目
若要將鍵盤快速鍵系結至自訂功能表命令，只要將專案新增至封裝的 *.vsct*檔案即可。 本主題說明如何將鍵盤快速鍵對應至自訂按鈕、功能表項目或工具列命令，以及如何在預設編輯器中套用鍵盤對應，或將它限制為自訂編輯器。

 若要將鍵盤快速鍵指派給現有的 Visual Studio 功能表項目，請參閱[識別及自訂鍵盤快速鍵](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。

## <a name="choose-a-key-combination"></a>選擇按鍵組合
 Visual Studio 中已經使用許多鍵盤快速鍵。 您不應該將相同的快捷方式指派給一個以上的命令，因為重複的系結很難偵測，而且也可能造成無法預期的結果。 因此，在您指派之前，最好先確認快捷方式的可用性。

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>若要確認鍵盤快速鍵的可用性

1. 在 **工具** > **選項** > **環境** 視窗中，選取 **鍵盤**。

2. 請確定已將中的 [**使用新的快捷方式**] 設定為 [**全域**]。

3. 在 [**按快速鍵**] 方塊中，輸入您要使用的鍵盤快速鍵。

    如果已在 Visual Studio 中使用快捷方式，則 [**目前使用的快捷方式**] 方塊會顯示快捷方式目前所呼叫的命令。

4. 請嘗試不同的索引鍵組合，直到找出未對應的按鍵。

   > [!NOTE]
   > 使用**Alt**的鍵盤快速鍵可以開啟功能表，而不是直接執行命令。 因此，當您輸入包含**Alt**的快捷方式時，box**目前使用的快捷方式**可能是空白的。您可以關閉 [**選項**] 對話方塊，然後按下按鍵，確認快捷方式沒有開啟功能表。

   下列程式假設您有一個具有功能表命令的現有 VSPackage。 如果您需要協助，請參閱[使用功能表命令建立擴充](../extensibility/creating-an-extension-with-a-menu-command.md)功能。

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>將鍵盤快速鍵指派給命令

1. 開啟您封裝的 *.vsct*檔案。

2. 在 `<Commands>` 之後建立空的 `<KeyBindings>` 區段（如果尚未存在）。

   > [!WARNING]
   > 如需金鑰系結的詳細資訊，請參閱[Keybinding](../extensibility/keybinding-element.md)。

    在 [`<KeyBindings>`] 區段中，建立 `<KeyBinding>` 專案。

    將 `guid` 和 `id` 屬性設定為您要叫用的命令。

    將 `mod1` 屬性設定為**Control**、 **Alt**或**Shift**。

    KeyBindings 區段看起來應該像這樣：

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   如果您的鍵盤快速鍵需要兩個以上的索引鍵，請設定 `mod2` 和 `key2` 屬性。

   在大部分的情況下，不應使用**Shift** ，而不需要第二個修飾詞，因為按它已經導致大部分的英數位元輸入大寫字母或符號。

   虛擬索引鍵代碼可讓您存取沒有與其相關聯之字元的特殊索引鍵，例如，函式索引鍵和**Backspace**鍵。 如需詳細資訊，請參閱[虛擬按鍵碼](/windows/desktop/inputdev/virtual-key-codes)。

   若要在 Visual Studio 編輯器中提供命令，請將 `editor` 屬性設定為 [`guidVSStd97`]。

   若要讓命令只能在自訂編輯器中使用，請在建立包含自訂編輯器的 VSPackage 時，將 `editor` 屬性設定為 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 封裝範本所產生的自訂編輯器名稱。 若要尋找 [名稱] 值，請在 [`<Symbols>`] 區段中尋找其 `name` 屬性以 "`editorfactory`" 結尾的 `<GuidSymbol>` 節點。這是自訂編輯器的名稱。

## <a name="example"></a>範例
 這個範例會將鍵盤快速鍵**Ctrl**+**Alt**+**C**系結至名為 `MyPackage`之套件中名為 `cmdidMyCommand` 的命令。

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
 這個範例會將鍵盤快速鍵**Ctrl**+**B**系結至名為 `TestEditor`的專案中名為 `cmdidBold` 的命令。 命令只能在自訂編輯器中使用，而不是在其他編輯器中提供。

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>請參閱
- [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)