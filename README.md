# CustomTweenService
A somewhat better alternative to Roblox's tween service. provides much better functionality with more easing directions. I created this module to provide tweening inside scripts.

> To begin, create CustomTweenInfo and assign arguments to it.
> Then require the module with the ease and style you want.
> Alternativly, you can require the main module and just provide 1 more argument to directly point to the needed ease style. I don't think it affects performance that much.
> Use Create() on the required module and fill the arguments it says to fill.
> Then use Play() on the created CustomTween.

(Don't forget it was designed to tween inside scripts in the first place, so if you want to tween parts, use RunService to assign value from the tween.)

## Showcase Code:

```lua
local TweenInterpolation = require(PathToModule)
local RunService = game:GetService("RunService")
local CustomTweenInfo = TweenInterpolation.CustomTweenInfo.new(0,false,0,5)
local CustomTween = TweenInterpolation:Create(
2,
Vector3.new(61,24,26),
Vector3.new(0,0,0),
TweenInterpolation.Enums.EasingStyle.Back,
TweenInterpolation.Enums.EasingDirection.OutIn,
CustomTweenInfo
)
task.wait(2)
CustomTween:Play()
local part = game.Workspace:FindFirstChildOfClass("BasePart")
part.Anchored = true
RunService.Heartbeat:Connect(function(DeltaTime)
    part.Position = CustomTween.Value
end)
```

# Properties of the provided classes:


## Module:


**Enums** - has every one of the custom ease styles/directions

**CustomTweenInfo** - makes the CustomTweenInfo "object", which has those arguments:

- **RepeatCount** - the number of times you want to repeat your tween

- **Reverses** - if set to true, then the value will be tweening backwards

- **DelayTime** - time between each repetition

- **Amplitude** = amplitude of the CustomTween (leave nil if you don't know what that is)

- **Period** = period of the CustomTween (leave nil if you don't know what that is)


## Tweening Module:


**Create()** - creates a new tween with the provided arguments:

- **Time** - provided duration of the CustomTween in seconds

- **StartingValue** - starting value you want to start tween with

- **EndValue** - ending value you want to end tween with

- **EasingStyle** (Main Module Only) - easing style you want to tween with

- **EasingDirection** - easing  direction you want to tween with

- **CustomTweenInfo** - custom tween info, self-explanatory


## Tween:
\
**Play()** - plays the tween
\
**Pause()** - pauses the tween
\
**Stop()** - stops the tween

### Tween properties:

**Completed** - sets to true after the tween is completed and after the tick turns back to false (in the feature I want to replace it with my Event-Emulator)

**Value** - output value that is being tweened

**TimeStamp** - time of the tween, 0- time provided in Create()

# Notes:

1. This work is based on: https://github.com/EmmanuelOga/easing
2. There is A LOT of potential to upgrade this module. Feel free to update it, just don't forget to paste the source link
3. I don't think it works on colors since they are different from the Vector3 number system
4. Report bugs immediately after you find one
