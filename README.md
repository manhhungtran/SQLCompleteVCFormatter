# Visual Commander Setup for SQL Complete Commands

This guide provides instructions on setting up a Visual Commander script to execute two SQL Complete commands (`FormatDocument` and `InsertSemicolons`) with a custom keyboard shortcut. This setup is intended specifically for T-SQL files and projects in Visual Studio.

Maybe this won't be needed in the future, but one project required inserting semicolons in every script, and it was annoying for me to do two things when formatting.

Here is a manual on how to make it work that was not generated:

## Prerequisites

Before proceeding, ensure that the following are installed:

1. **Visual Studio 2022** (or later)
2. **SQL Complete** extension for Visual Studio
   - Install SQL Complete from the [Devart website](https://www.devart.com/sqlcomplete/).
3. **Visual Commander** extension for Visual Studio
   - Install Visual Commander from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=SergeyVlasov.VisualCommander).
   - For this free version is enough

Once Visual Studio, SQL Complete, and Visual Commander are installed, you can go ahead with the following steps.

## Step 1: Import the Visual Commander Command via Import

To quickly import the prepared Visual Commander command, follow these steps:

1. **Download the Command Script**:
   - Visit the following URL: [https://github.com/manhhungtran/SQLCompleteVCFormatter/blob/main/sqlcomplete-format.vcmd](https://github.com/manhhungtran/SQLCompleteVCFormatter/blob/main/sqlcomplete-format.vcmd).
   - Right-click on the `Raw` button and choose **Save link as** to download the `.vcmd` file.
   - Navigate to `Extentions` > `VCmd` > `Import...` to import this file.
   - Find previous saved file
   - Done

## Step 2: Map the Command to a Hotkey

1. Go to `Tools` > `Options` in Visual Studio.
2. Navigate to `Environment` > `Keyboard`.
3. In the **"Show commands containing"** box, type the name of the command you just imported (it is always `VCmd.Command01` if you did not use this tool previously).
4. Select the command from the list.
5. In the **"Press shortcut keys"** box, press `Ctrl + K, D` (or your preferred key combination).
6. Click **Assign** to assign the shortcut, then click **OK** to save the changes.

### Restrict the Hotkey to T-SQL Files and Projects

To ensure that the hotkey is only active for T-SQL files and projects, confirm that the project or file being edited is a T-SQL file (e.g., `.sql`, `.tsql`). While Visual Studio does not allow for direct hotkey restrictions based on file types, the hotkey will only work when the relevant T-SQL file is focused.

## Step 3: Unassign the Default SQL Complete Hotkey for `FormatDocument`

To avoid conflicts with the default SQL Complete hotkey, unassign the `SQLComplete.FormatDocument` hotkey:

1. Go to `Tools` > `Options` in Visual Studio.
2. Navigate to `Environment` > `Keyboard`.
3. In the **"Show commands containing"** box, type `SQLComplete.FormatDocument`.
4. If a shortcut is assigned, it will appear in the **"Press shortcut keys"** section.
5. Select the `SQLComplete.FormatDocument` command.
6. Click **Remove** to unassign the hotkey.
7. Click **OK** to save the changes.

### Notes:
- If the script does not work immediately after setup, restarting Visual Studio may help apply the changes.
- The Visual Commander script can be further customized to add more SQL Complete commands or adjust its behavior as needed.
