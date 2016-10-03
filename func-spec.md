# Overview

Roobish is a turn-based strategy game for the browser. It's a cross between a classic RPG battle system and an online collectible card game.

A key design goal is for the outcome of every match to be decided purely on the decisions made by the players, without any influence from luck and/or an uneven playing field. In other words, there's no impactful RNG during games, there's no concept of being matched up against a "counter" as part of the matchmaking process, and players never gain advantages by paying money or playing a lot.

# Game Modes

Roobish v1.0 will only include a single game mode: Yolo.

Future game modes under consideration are: Classic, Gauntlet, Adventure, and Trainer.

## Yolo Mode

This mode is a head-to-head match between two players using randomly selected monsters. Before the match begins, two teams are randomly generated with four monsters each. It's not possible for two instances of the same monster to appear on the same team, but there can be two instances of the same monster in the match, with one instance on each team.

The match consists of two rounds. Each player controls each team of monsters for one round. The game state is completely reset between rounds at the same time that players swap teams. This system ensures that neither player gains an advantage from having better monsters than their opponent.

The winner of the match is the player with the highest score after both rounds.

This mode is available in both the PvP and PvE variety. In v1.0, PvP matchmaking will consist of a simple first-come, first-serve. Future releases will introduce a rating system as well as the ability to battle a friend.

## Classic Mode

This mode is under consideration for a future release. It's exactly the same as Yolo Mode except that instead of being assigned randomly generated monsters, players select their monsters ahead of time in isolation. However, just like in Yolo Mode, a match consists of two rounds, and after the first round, the game state resets and players swap teams, ensuring that neither player gains an unfair advantage due to having better monsters or being matched up against a counter.

## Gauntlet Mode

This mode is under consideration for a future release. It's a PvE-only mode, although players are encouraged to compete with each other indirectly via a leader board.

At the beginning of each day, 16 monsters are randomly selected. Duplicates are allowed as long as there are no more than four instances of any given monster. These are the gauntlet monsters for the rest of the day. The daily gauntlet monsters are the same for all players.

Prior to beginning the match, the player and computer must each create four teams of four monsters using their own instances of the 16 daily gauntlet monsters. The only restriction is that no single team can contain more than one of the same monster. The computer always splits its monsters up in the exact same way for all players. However, players are free to switch their teams up between matches if they play more than once.

A gauntlet match consists of four rounds between the player and computer. At the start of each round, the player and computer select which of their four teams they will use. Each team can only be selected once during the match. The computer always selects its teams in the same order for all players. As with Yolo mode, the game state is completely reset between rounds. However, unlike Yolo mode, there is no need to swap teams.

A daily leader board keeps track of the highest four-round scores across all players.

## Adventure Mode

This mode is under consideration for a future release. It's a PvE-only mode, although players can trade monsters with other players.

This mode allows players to collect monsters and go on dungeon crawls with their collected monsters.

## Trainer Mode

This mode is under consideration for a future release. It allows players to program their monsters using the same language that's used to program the computer's AI. Players then pit their programmed monsters against monsters programmed by other players or the computer. This means that players watch matches instead of participating in them.

Players can also place bets on matches using in-game currency.

Players can also queue up their team in the morning, and without any further interaction at all, have their team continue to do battle throughout the day, collecting rewards.

# Battle System

## Overview

Although there are multiple game modes planned that differ in terms of how many battles there are in a match, or how monster teams are selected, the actual battle system remains consistent across all of them. It's possible that future game modes will feature unique variations of this battle system, but such variations will be documented separately.

## Matches

A match is a series of one or more battles. The exact number of battles depends on the game mode. You play against the same opponent for each battle, although many game modes involve changing monsters after each battle.

The master with the highest cumulative match score after all battles are finished is declared the winner of the match. If both you and your opponent have the same match score, then the match ends in a tie. There's no tiebreaker, primarily because it'd take too long; it's a design goal for yolo matches to take a predictable amount of time to complete. Due to the way scoring works, ties will be a rare occurrence.

## Battles

A battle consists of a variable number of turns. Each battle begins with a fresh game state. Therefore, it's appropriate to think of battles in Roobish as being similar to rounds in a fighting game like Mortal Kombat. The only value that's tracked across multiple battles is each master's cumulative match score.

At the start of a battle, your four monsters are placed on the battlefield in the passive position. Your opponent's four monsters are placed across from your monsters, also in the passive position. You can see your opponent's monsters, and vice versa. These are the only monsters that will be involved in the current battle. These monsters are all in a completely fresh state, even if they were used in previous battles.

You and your opponent each have a portal. Both portals are in a completely fresh state, as explained in the **Portals** section.

The battle ends at the end of a turn when at least one master's portal's **Summon Energy** is at 0 or less. Since the battle doesn't end until the end of the turn, it's possible for the **Summon Energies** of both master's portal's to be at 0 or less.

The master with the higher **Summon Energy** at the end of the battle is awarded match points equal to the difference in **Summon Energies** between the two portals. If the **Summon Energies** of both portals are at 0, and are equal, then the battle still ends, but no match points are awarded.
