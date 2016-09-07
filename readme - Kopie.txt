The following needs to be done to capture this video in full quality again:

1)  Modify config files to load full textures in full resolution:
    Open frontend\SecretAge\Config\DefaultDeviceProfiles.ini
    in the section [Windows DeviceProfile]
    in the lines TEXTUREGROUP_World and TEXTUREGROUP_Character
    set LODBias=-2 and MaxLODSize=2048

2)  Modify the Master Character Material so the characters cast shadows:
    Open in the editor: frontend\SecretAge\Content\Shared\Materials\Character\M_MasterCharacter.uasset
    Set the blend mode to opaque and enable two sided

3)  If there are issues with the depth of field effect, make sure temporal antialiasing is activated in the project settings.



To render to green screen version:

1)  Make the Green screens visible:
    In the editor, world outliner search for GreenScreen
    enable the visible flag of the green screen actors

2)  Hide the background:
    Open the levels window
    Right click the sub level and change the streaming method to "blueprint".
    Click the eye icon of the sub level to hide it in the editor

3)  Disable Depth of field:
    In the post process volume set DoF Method to "Bokeh DoF" (Which disables it in this case)



To render the scene depth version:

1)  Assign a scene depth blendable to the post process volume:
    In the Content Browser click the view options in the lower right corner and check "Show engine content"
    In the engine content folder find "SceneDepth"
    Find the PostProcessVolume actor in the level
    Open its Post Process Volume / Settings / Blendables tab
    Add a new item and assign "SceneDepth" from the content browser
