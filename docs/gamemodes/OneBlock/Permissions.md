# OneBlock Permissions

```
permissions:    
  oneblock.island:
   description: Allow island command usage
   default: true
  oneblock.island.create:
    description: Allow island creation
    default: true
  oneblock.island.home:
    description: Allow teleporting to player island
    default: true
  oneblock.island.sethome:
    description: Let the player use the sethome command
    default: true
  oneblock.island.info:
    description: Let the player check other players info
    default: true
  oneblock.island.lock:
    description: Allows island locking
    default: true
  oneblock.island.near:
    description: Players can see nearby island names
    default: true
  oneblock.island.expel:
    description: Allows expelling of visitors
    default: true
  oneblock.island.ban:
    description: Allows banning of visitors
    default: true
  oneblock.island.settings:
    description: Player can see server settings
    default: true
  oneblock.island.language:
    description: Player can select a language
    default: true
  oneblock.island.name:
    description: Player can set the name of their island
    default: true
  oneblock.island.spawn:
    description: Player can use the island spawn command if spawn exists
    default: true
  oneblock.island.reset:
    description: Player can use the island reset or restart command
    default: true  
  oneblock.island.team:
    description: Let a player use team command
    default: true
  oneblock.island.team.setowner:
    description: Let a player change the team owner
    default: true
  oneblock.island.team.invite:
    description: Let a player invite others
    default: true
  oneblock.island.team.reject:
    description: Let a player reject invites
    default: true
  oneblock.island.team.leave:
    description: Let a player leave the team
    default: true
  oneblock.island.team.kick:
    description: Let a player kick team members
    default: true
  oneblock.island.team.accept:
    description: Let a player accept invitations
    default: true
  oneblock.island.team.trust:
    description: Let a player use team trust commands
    default: true
  oneblock.island.team.coop:
    description: Let a player use team coop commands
    default: true
  oneblock.island.team.promote:
    description: Let a player use promote commands
    default: true
  oneblock.settings.*:
    description: Allow use of settings on island
    default: true
  oneblock.mod.info:
    description: Let a moderator see info on a player
    default: op
  oneblock.mod.clearreset:
    description: Allow clearing of island reset limit
    default: false
  oneblock.mod.bypasscooldowns:
    description: Allow moderator to bypass cooldowns
    default: op
  oneblock.mod.bypassdelays:
    description: Allow moderator to bypass delays
    default: op
  oneblock.mod.bypassprotect:
    description: Allow moderator to bypass island protection
    default: op
  oneblock.mod.bypassexpel:
    description: Allow moderator to bypass island expulsion
    default: op
  oneblock.mod.switch:
    description: Allows moderator to switch bypass protection on and off
    default: op
  oneblock.mod.lock:
    description: Locks or unlocks an island
    default: op
  oneblock.mod.bypasslock:
    description: Bypasses an island lock
    default: op
  oneblock.mod.bypassban:
    description: Bypasses island ban
    default: op  
  oneblock.mod.team:
    description: Enables modification of teams via kick and add commands
    default: false
  oneblock.admin.tp:
    description: Allows teleport to an island
    default: op    
  oneblock.admin.clearresetall:
    description: Allow clearing of island reset limit of all players
    default: op
  oneblock.admin.reload:
    description: Reload the config.yml
    default: op
  oneblock.admin.delete:
    description: Let a player completely remove a player (including island)
    default: op
  oneblock.admin.register:
    description: Let a player register the nearest island to another player.
    default: op
  oneblock.admin.unregister:
    description: Removes a player from an island without deleting the island blocks.
    default: op
  oneblock.admin.setspawn:
    description: Allows use of spawn tools
    default: op
  oneblock.admin.setrange:
    description: Allows setting of island protection range
    default: op
  oneblock.admin.settingsreset:
    description: Resets all the islands to default protection settings
    default: op
  oneblock.admin.noban:
    description: Player cannot be banned from an island
    default: op
  oneblock.admin.noexpel:
    description: Player cannot be expelled from an island
    default: op
  oneblock.admin.setlanguage:
    description: Resets all player languages and sets the default language
    default: op
  oneblock.admin.getrank:
    description: Get a player's rank
    default: op
  oneblock.admin.setrank:
    description: Set a player's rank
    default: op
  oneblock.admin.setchest:
    description: Puts the looked-at chest into a phase with a given rarity
    default: op
 ``` 