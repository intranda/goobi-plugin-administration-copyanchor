### Goobi Adminplugin to copy Master-Anchor files into all volumes


## Installation
First place the plugin and the GUI file into their appropiate locations:
```sh
mv plugin_intranda_administration_Linz-GUI.jar /opt/digiverso/goobi/plugins/GUI/
mv plugin_intranda_administration_Linz-GITHASH.jar /opt/digiverso/goobi/plugins/administration/
```

Then you need to define a metadata called `InternalNote` in the ruleset file and add it to the volume. Example:

```xml
  <MetadataType>
    <Name>InternalNote</Name>
    <language name="de">Interne Goobi-Anmerkung</language>
    <language name="en">Internal Note for Goobi</language>
  </MetadataType>


  <DocStrctType topStruct="true">
    <Name>PeriodicalVolume</Name>
    <language name="de">Zeitschriften-Band</language>
    <language name="en">Periodical Volume</language>
    <!-- more here -->
    <metadata num="*">InternalNote</metadata>
  </DocStrctType>
```

## Usage
Login to Goobi and take a volume that you would like to become a Master Anchor. Open the METS-Editor, add a new metadata `InternalNote` and add as value `MasterAnchor`. Make the desired changes to the anchor and copy the Identifier of the anchor. Safe and exit.

Switch to "Administration" -> "AnchorCopyPlugin", add the identifier to the only available input box and hit "copyAnchorFileToProcesses".

