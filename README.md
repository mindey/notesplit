# Usage.

Running `python split.py -s OnePage.wiki -g GroupDefinitions.wiki` will split a source file `OnePage.wiki` and copy it to the folders defined in `GroupDefinitions.wiki`, implementing sharing with one friend, sharing with group of friends, or sharing with group and excluding parts of the content from a particular friend, or another group (group intersections).

## User story
Imagine that you write your private diary in a text file, and want to share a part of it with someone else's diary.

**OnePage.wiki**
```
This is your private wiki... 

By default, the diary is your private diary... 
Unless, you want {:all|SOMETHING:} all of your friends
to see, or one of your friends to see {:friend1| JUST FOR YOU :},
or a group of friends to see, say {:group1| MY DEAR ONES :}. 

Or, you sometimes want to share with a group, but exclude someone, or some subgroup:

{:group1|
== Example Story ==
One day, I realized that we could use shared diaries on VIM, and I hacked a solution to let my dear friend also see my diary. We started writing diaries together, side-by-side, every day. We share them via Dropbox, but encrypted, and using gnupg plugin for VimWiki.

It is a wonder to share minds like that together. I think it is like being two hemispheres of brain, connected via corpus callosum. We merged to form something new! Two minds working in unison.

{:-group2|Then. We thought we should share more with our friends, and we found BTSync, which is like Dropbox, but P2P. It was the solution, because we didn't need to teach every friend how to use GPG and VIM. However, there is a little problem that we would like to fix, but have no time right now.:}

We already have a Python script {:-friend1|( https://github.com/Mindey/diary-scripts/blob/master/diary-cron.py ) :}that does something similar. We would like to have a general solution, which goes as deep into the hierarchy defined by nested braces {: :} as needed to parse them.
:}

```

This is your groups..

```
{
    "individuals": {
        "friend1": "./wiki/friend1",
        "friend2": "./wiki/friend2",
        "friend3": "./wiki/friend3"
    },
    "groups": {
        "all": ["friend1", "friend2", "friend3"],
        "group1": ["friend1","friend2"],
        "group2": ["friend2"]
    }
}
```

You get the splits made into the folders defined, and then, you can use something like [syncthing](https://syncthing.net/) to synchronize each of the folders with specific friends.
