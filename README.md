# manjarno
Repository which documents some reasons for not using Manjaro.

__Disclaimer__: I don't _hate_ Manjaro. These are some reasons
which made me consider shifting to a different distro. However, 
I still believe that Manjaro is a good starting point for 
beginners who want to explore an Arch <strike>based</strike> 
_like_ distro.

__Note__: To clarify my stance, I should state what I use personally.
I use Endeavour OS, which uses Arch repositories directly.
They maintain a separate 
[repository](https://github.com/endeavouros-team/PKGBUILDS) for 
distributing packages for theming, some small utilities and 
drivers - none of which override any packages in Arch mainline
repositories.

## Package Repository issues

Manjaro maintains a separate repository that is not in sync with Arch's
main repositories which means Manjaro is not *just* Arch. To add to that,
even Manjaro wiki states that it is not Arch [1]! To quote the wiki,

> In fact, the differences between Manjaro and Arch are far greater than
> the differences between the popular Ubuntu distribution and its many
> derivatives, including Mint and Zorin.

(Yes, Manjaro isn't Arch and Manjaro users _shouldn't_ use the _"btw"_
line. However, I don't really care.)

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

Their own updater had a serious security vulnerability which has fortunately 
been fixed [2]. This is actually a core package, not an extra or
community package. To quote the list,

> I have discovered an issue with one of your core Manjaro packages,
> `manjaro-system` 20180716-1 and earlier.
> The issue allows a local attacker to execute a Denial of Service,
> Arbitrary Code Execution, and Privilege Escalation attack.

The amount of attacks that could have been done due to this vulnerability is a
lot!

In an update, password less updates in pamac (Manjaro's AUR helper)
were sneaked in and from the look in the issue [4] made concerning this,
the change was made to look like a "feature". This is a major security
issue considering that packages in AUR are not checked by Arch Linux
maintainers (and Manjaro does not maintain its own either). Some AUR
packages were found to be malware in the past. So think about a casual
user (Manjaro's target demographic are not really power users) installing
a harmless-looking AUR package that could potentially mess up their system!

### Other problems in the Manjaro system updater 

The Manjaro updater [3] does all the bad practices that one could do in
a general Linux system and Arch Linux system specifically. Each time
the system updates, they reinstall some packages to "fix" issues and
they use the `--no-confirm` flag (force) every time they do so and
various other odd sequences of commands which are just as bad, if not
more.

## SSL Certificates
Manjaro let their SSL certificates expire not once, not twice, not thrice, but four times [5]!
The first time, they asked the users to use a private window and/or change
the system time [6].
The second time when the SSL certificates expired, they did the same [7].
The third SSL certificate expiration was handled a little more sanely[8].
The fourth time, HSTS was set but the website was still down [16].

## DDoS'ing the AUR

On 2021-04-26, the AUR (Arch User Repository) was DDoS'd by a bad version
of pamac, which is the default Graphical Package Manager for Manjaro [9].

On 2021-10-14, Pamac was once again blocked by the AUR for shipping another bad version that flooded the AUR with requests [10, 11].


## Links
[1] https://wiki.manjaro.org/index.php?title=Manjaro:_A_Different_Kind_of_Beast

[2] https://lists.manjaro.org/pipermail/manjaro-security/2018-August/000785.html

[3] https://gitlab.manjaro.org/packages/core/manjaro-system/blob/master/manjaro-update-system.sh#L34

[4] https://gitlab.manjaro.org/applications/pamac/issues/719

[5] https://www.reddit.com/r/linuxquestions/comments/wqzrpl/did_manjaro_just_forget_to_renew_the_ssl/

[6] https://web.archive.org/web/20150409112614/https://manjaro.github.io/

[7] https://web.archive.org/web/20160512210401/https://manjaro.github.io/

[8] https://gitlab.manjaro.org/applications/pamac/-/issues/1017

[9] https://web.archive.org/web/20220102232338/https://forum.manjaro.org/t/expired-certificate-for-iso-download-on-download-manjaro-org/96441

[10] https://redd.it/q85t8n/

[11] https://gitlab.manjaro.org/applications/pamac/-/issues/1135

[12] https://archived.forum.manjaro.org/t/manjaro-is-taking-the-next-step/102105

[13] https://opencollective.com/manjaro/expenses/new (Will show a login prompt, policy can be seen on the right side of the page without logging in)

[14] https://opencollective.com/manjaro/expenses/22477

[15] https://web.archive.org/web/20200807042341/https://forum.manjaro.org/t/change-of-treasurer-for-manjaro-community-funds/154888

[16] https://manjarno.snorlax.sh/expiry-2022-08-17.png
