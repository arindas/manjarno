# manjarno
Repository which documents some reasons for not using Manjaro.

## Manjaro isn't Arch
(which isn't the main issue by itself; the problems introduced are)

A lot of Manjaro users I have talked to say that Manjaro is just Arch
with an installer. However, this is fundamentally wrong!

Manjaro maintains a separate repository which is not in sync with Arch's
main repositories which means Manjaro is not *just* Arch. To add to that,
even Manjaro wiki states that it is not Arch [1]! To quote the wiki,

> In fact, the differences between Manjaro and Arch are far greater than
> the differences between the popular Ubuntu distribution and its many
> derivatives, including Mint and Zorin.

### Own repository
Manjaro claims to be stable just by delaying packages for a week. This
is not an approach a stable distribution would take at all!

### The problems introduced
If Manjaro had to be actually stable, it needs to hold back the AUR packages
as well. It has to maintain its AUR that is in sync with the Manjaro repos.

Say that a package in the AUR depends on a library, say libxyz. And libxyz is
in the main repos, not in the AUR. The package is updated so that it relies
on the new features introduced in libxyz's version 1.1 however Manjaro delays
packages so libxyz is still on 1.0 in Manjaro. If you update the package in
Manjaro, it will break because Manjaro holds back packages. So the only
way Manjaro can be stable is by literally forking all the Arch related
repositories including the AUR and keeping them in sync.

## Security
Manjaro is not really a secure distro.

Their own updater had a security vulnerability which wasn't fixed
until recently [2]. This is actually a core package, not an extra or
community package. To quote the list,

> I have discovered an issue with one of your core Manjaro packages,
> `manjaro-system` 20180716-1 and earlier.
> The issue allows a local attacker to execute a Denial of Service,
> Arbitrary Code Execution, and Privilege Escalation attack.

The amount of attacks that can be done due to the vulnerability is a
lot!

The Manjaro updater [3] does all the bad practices that one could do in
a general Linux system and Arch Linux system specifically. Each time
the system updates, they reinstall some packages to "fix" issues and
they use the `--no-confirm` flag (force) everytime they do so and
various other odd sequence of commands which are just as bad, if not
more.

In an update, password less updates in pamac (Manjaro's AUR helper)
were sneaked in and from the look in the issue [4] made concerning this,
the change was made to look like a "feature". This is a major security
issue considering that packages in AUR are not checked by Arch Linux
maintainers (and Manjaro does not maintain its own either). Some AUR
packages were found to be malware in the past. So think about a casual
user (Manjaro's target demographic are not really power users) installing
a harmless-looking AUR package that could potentially mess their system!

## SSL Certificates
Manjaro let their SSL certificates expire not once but twice [5]!
The first time, they asked the users to use a private window and/or change
the system time [6].
The second time when the SSL certificates expired, they did the same [7].

## DDoS'ing the AUR

On 2021-04-26, the AUR (Arch User Repository) was DDoS'd by a bad version
of pamac, which is the default Graphical Package Manager for Manjaro [8].

## Fishy Finances

It appears that, in September of 2019, Manjaro switched from holding community donations in Philip Müller's personal bank account to accounts being held by OpenCollective and CommunityBridge [9]. This change also brought on Jonathon Fernyhough as treasurer. There is also a policy in place that requires all expenses to be discussed on approved channels and nominally approved prior to any purchases [10]. On (or around) July 24th of 2020, a request for a \$2,000 laptop was made by Philip for developer Helmut Stult [11].  Johnathon rejected this expense due to lack of prior discussion and questioned the expense [13]. The role of treasurer is now back fully in Philip's hands, and has approved the \$2,000 laptop.  This draws questions on the integrity of Philip's leadership.

Further discussions and sources:

- https://linuxreviews.org/Manjaro_Linux_Lead_Developer_In_Hot_Waters_Over_Donation_Slush_Fund_For_Laptop_And_Personal_Items
- https://www.reddit.com/r/ManjaroLinux/comments/hwo33h/change_of_treasurer_for_manjaro_community_funds/
- https://www.reddit.com/r/linux/comments/hwoev3/change_of_treasurer_for_manjaro_community_funds/
- https://web.archive.org/web/20200807042341/https://forum.manjaro.org/t/change-of-treasurer-for-manjaro-community-funds/154888

## Links
[1] https://wiki.manjaro.org/index.php?title=Manjaro:_A_Different_Kind_of_Beast

[2] https://lists.manjaro.org/pipermail/manjaro-security/2018-August/000785.html

[3] https://gitlab.manjaro.org/packages/core/manjaro-system/blob/master/manjaro-update-system.sh#L34

[4] https://gitlab.manjaro.org/applications/pamac/issues/719

[5] https://www.reddit.com/r/linux/comments/4inrut/manjaros_ssl_certificate_expired_again/

[6] https://web.archive.org/web/20150409112614/https://manjaro.github.io/

[7] https://web.archive.org/web/20160512210401/https://manjaro.github.io/

[8] https://gitlab.manjaro.org/applications/pamac/-/issues/1017

[9] https://archived.forum.manjaro.org/t/manjaro-is-taking-the-next-step/102105

[10] https://opencollective.com/manjaro/expenses/new (Will show a login prompt, policy can be seen on the right side of the page without logging in)

[12] https://opencollective.com/manjaro/expenses/22477

[13] https://web.archive.org/web/20200807042341/https://forum.manjaro.org/t/change-of-treasurer-for-manjaro-community-funds/154888
