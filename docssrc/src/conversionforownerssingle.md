# Single command conversion

Often, you don't want to convert _every single command_ that a plugin declares, and instead you only want to convert a few commands that a plugin has.

To convert a single command, you need to first populate the `config.yml` with the name of the plugin and commands to be converted. To illustrate this, we'll use an example:

<div class="example">

### Example - Converting commands

Say we're using [EssentialsX](https://www.spigotmc.org/resources/essentialsx.9089/) on our server and we want to be able to use `/afk` and `/hat` in command blocks. This would allow us to use (for example) the following commands in command blocks:

```
/execute as @p run afk
/execute as @p run hat
```

To do this, we need to add `Essentials` to our `config.yml` file, and include the commands `afk` and `hat` as the commands to be converted from the Essentials plugin. This would then make our `config.yml` file look like this:

```yaml
verbose-outputs: true
create-dispatcher-json: false
plugins-to-convert: 
  - Essentials: 
    - hat
    - afk
```

> **Developer's Note:**
>
> Note that the commands `hat` and `afk` are used, as opposed to an alias such as `head`. The CommandAPI is only able to convert plugin commands that are declared in a plugin's `plugin.yml` file. For example, if we take a look at the EssentialsX `plugin.yml` file, we can see the commands `afk` and `hat` have been declared and thus, are the commands which must be used in the CommandAPI's `config.yml` file:
>
> ```yaml
> name: Essentials
> main: com.earth2me.essentials.Essentials
> version: 2.18.0.0
> website: http://tiny.cc/EssentialsCommands
> description: Provides an essential, core set of commands for Bukkit.
> softdepend: [Vault, LuckPerms]
> authors: [Zenexer, ementalo, Aelux, Brettflan, KimKandor, snowleo, ceulemans, Xeology, KHobbits, md_5, Iaccidentally, drtshock, vemacs, SupaHam, md678685]
> api-version: "1.13"
> commands:
>   afk:
>     description: Marks you as away-from-keyboard.
>     usage: /<command> [player/message...]
>     aliases: [eafk,away,eaway]
> 
> # (other config options omitted)
> 
>   hat:
>     description: Get some cool new headgear.
>     usage: /<command> [remove]
>     aliases: [ehat,head,ehead]
> 
> # (other config options omitted)
> ```

</div>

-----