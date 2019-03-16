## AV-Circle-Numbers

__AV-Circle-ID__ is intended to be an opentype ready font with glyph substituion enabled in the opentype feature calt. It currently doesn't work. 

__AV-CircleNumberFaces__ is a family that provides the circle forms in their regular low ascii positions, to allow manual manipulation by changing the font style (regular, italic, bold, bold-italic.) 


__Background: How this font came to be.__

For the proposed appearance as footnote callers with circles, the fonts method may be the easiest, because it can be acheived with font substitution. We did this (sort of) to acheive circle number footnote markers in a CJK text, by moving circle glyphs into a-z ascii locations, and using indesign a-z marker style. With that method, correct display was limited to no more than 26 notes per page, so the method worked for print, but would have been trouble to use Indesign as a base for digital distribution, which was our plan at the time. 

A Similar process will allow multiple digit footnote callers to appear with rings. You'll need to grep style initial numbers to open the circle, and grep style final numbers to close the circle.  Since grep styling has to be done in paragraph styles, you'll need to be careful. 

To implement the substitution in Indesign You'll need: 

1. A font like AV-CircleNumbersFaces.

2. Define 4 indesign character styles that map to these four faces. 
    + vo - isolated (complete) circle numbers mapped to unicode 0-9 (u0030-u0039)
    + vi - initial verse semicircle glyphs mapped to unicode 0-9
    + vm - medial high-low lines and digit glyphs mapped to unicode 0-9 
    + vf - final verse semicircle digit glyphs mapped to unicode for 0-9

3. In your default paragraph style, define grep styles for verse and footnote marker digits in character style v
    (I don't have indesign handy, but you want to define the v style to use medial font face, then grep for the first and last digit. Do the grep for isolated last.)

_______

And since I hit send... this seems like a medieval solution for 2019. Initial-medial-final isolated rendering is baked into any good text composer these days.The font I pointed to before probably has an opentype feature that does all the work I suggest doing by grep style and relocating glyphs. I don't have that font, but I suspect it provides a much simpler solution that involves:

a. setting the verse number style to a specific language, 

b. enabling the contextual alternates (calt) feature for that style, 

c. and using world ready composer in Indesign. 

This is all a guess. but if you go down this path, look for a simple solution like in this second email before building the grep monster I described before.  

________

Follow up: circled verse and footnote callers via contextual alternate font. 

 I went investigating and it seems there is no solution like I described (turning on contextual alternates to get multiglyph callers ringed for eastern typography.) 

So I pulled the circle numbers out of the Stix Math font and have built glyphs to prove this works. And It works (I know sans is preferred in eastern typography ornaments... sorry the serif set in the Stix font was more complete... and this is just a proof of concept to myself anyway.) 

And I've found a brick wall of setting up contextual alternates. 

contextual alternates are common with middle eastern and indic fonts.. This should be easy to set up, I'm just not a fontographer. Is someone on this list willing to provide an example calt table with enough in it that I can build a calt table for a font as described above?  Not the whole table, just enough structure so I can fill this in?

________

> curious why the focus on contextual alternates (calt in OpenType). In Harmattan, for example, calt is used for different glyphs associated with different languages. You can see calt used on line 1137 of https://github.com/silnrsi/font-harmattan/blob/master/source/opentype/master.feax

The CALT  feature allows for things like exchanging glyphs if certain conditions are true, such as a language is X, but also it can exchange when the preceeding or following character is a digit or whitespace. Because this solution sticks to the font, I think "do it once, do it right" applies. If the font manages it, then the app doesn't have to, and the solution ports to any opentype enabled app. 

However, after reading up on it more, enabling contextual alternates for initial, medial, isolated, final forms is apparently step 4 or 5 down a path, and I'm trying to skip some steps.  So, back to school. :-) 

https://docs.microsoft.com/en-us/typography/script-development/arabic

My selfish motivation WHY I'm fixating on embedding solutions into the font is that I'm designing typesets with LibreOffice, which doesn't have the grepstyle capability in the app, but does support opentype and graphite, so the calt table is the only method to swap in these alternate glyphs without a lot of manual precomposition work, and the only way for it work and maintain text integrity (where verse numbers paste into other apps as numbers.) 
