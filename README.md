# Visual Commander Setup for SQL Complete Commands

This guide provides instructions on setting up a Visual Commander script to execute two SQL Complete commands (`FormatDocument` and `InsertSemicolons`) with a custom keyboard shortcut. This setup is intended specifically for T-SQL files and projects in Visual Studio.

Maybe this won't be needed in the future, but one project required inserting semicolons in every script, and it was kinda annoying for me to do two things when formatting.

Here is manual how to make it work that was totally not generated:

## Prerequisites

Before proceeding, ensure that the following are installed:

1. **Visual Studio 2022** (or later)
2. **SQL Complete** extension for Visual Studio
   - Install SQL Complete from the [Devart website](https://www.devart.com/sqlcomplete/).
3. **Visual Commander** extension for Visual Studio
   - Install Visual Commander from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=SergeyVlasov.VisualCommander).

Once Visual Studio, SQL Complete, and Visual Commander are installed, proceed with the following steps.

## Step 1: Import the Visual Commander Script

1. Open **Visual Studio**.
2. Navigate to `Tools` > `Visual Commander` to open the Visual Commander window.
3. In the **Visual Commander** window, go to the **Commands** tab and click **Add Command**.
4. Copy and paste the following C# script into the editor - or download and import this script that is in this repository:

    ```csharp
    using EnvDTE;
    using EnvDTE80;

    public class C : VisualCommanderExt.ICommand
    {
        public void Run(EnvDTE80.DTE2 DTE, Microsoft.VisualStudio.Shell.Package package)
        {
            // Execute SQL Complete commands
            DTE.ExecuteCommand("SQLComplete.FormatDocument");
            DTE.ExecuteCommand("SQLComplete.InsertSemicolons");
        }
    }
    ```

5. Click **Save** to store the command. You can name it `FormatSQLAndInsertSemicolons` or another preferred name.

## Step 2: Map the Command to a Hotkey

1. Go to `Tools` > `Options` in Visual Studio.
2. Navigate to `Environment` > `Keyboard`.
3. In the **"Show commands containing"** box, type the name of the command you just created (e.g., `FormatSQLAndInsertSemicolons`).
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

This will ensure that the new hotkey you assigned will not conflict with the default `SQLComplete.FormatDocument` command.

## Conclusion

This setup provides a custom Visual Commander script that runs two SQL Complete commands (`FormatDocument` and `InsertSemicolons`) using a custom hotkey for T-SQL files. The default SQL Complete hotkey for `FormatDocument` has been unassigned to prevent conflicts.

### Notes:
- If the script does not work immediately after setup, restarting Visual Studio may help apply the changes.
- The Visual Commander script can be customized to add more SQL Complete commands or adjust its behavior as needed.
