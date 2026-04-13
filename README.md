# GGUI

## TutorialButton

`GGUI.TutorialButton` can now drive both classic `HelpPlate` overlays and modern `HelpTip` bubbles.

### HelpPlate mode

```lua
local tutorialButton = GGUI.TutorialButton({
	parent = MyFrame,
	anchorPoints = {
		{ anchorParent = MyFrame, anchorA = "TOPRIGHT", anchorB = "TOPRIGHT", offsetX = -8, offsetY = -8 },
	},
	helpPlateInfo = MyHelpPlateInfo,
	helpPlateParent = MyFrame,
	glowOnInit = true,
})

-- Optional explicit controls:
tutorialButton:ShowHelpPlate()
tutorialButton:HideHelpPlate(true)
tutorialButton:ShowTutorialTooltip()
```

### HelpTip mode

```lua
local tutorialButton = GGUI.TutorialButton({
	parent = MyFrame,
	anchorA = "TOPRIGHT",
	anchorB = "TOPRIGHT",
	helpTipParent = MyFrame,
	helpTipRelativeRegion = MyFrame.SomeRegion,
	helpTipInfo = {
		text = "Explain this control",
		buttonStyle = HelpTip.ButtonStyle.GotIt,
		targetPoint = HelpTip.Point.BottomEdgeCenter,
		alignment = HelpTip.Alignment.Center,
	},
})

-- Toggle uses the configured help data automatically.
tutorialButton:ToggleHelpTip()
```

### Notes

- Default click behavior is inferred automatically:
  - `helpPlateInfo` set -> toggles HelpPlate
  - `helpTipInfo` set -> toggles HelpTip
  - neither set -> callback-only button
- `clickCallback` can return `true` to fully handle the click and prevent auto toggle.