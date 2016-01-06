# Computer_Graphics_Ray_Tracer
```html
<!DOCTYPE html>
<html>
  <head>
    <meta content="text/html; charset=windows-1252" http-equiv="content-type">
    <title>FinalProject CSC513 - Ray Tracer - Vy Bui</title>
  </head>
  <body>
    <h1 style="text-align: center;">The Catholic University of America</h1>
    <h1 style="text-align: center;">Final Project CSC513</h1>
    <h2 style="text-align: center;">Vy Bui</h2>
    <h2 style="text-align: center;">Dec 04, 2014</h2>
    <h1 style=" text-align: center;"><span style="color: red;">Ray Tracer </span></h1>
    <div style="text-align: center;"><img alt="" src="Fullscreen%20capture%201242014%20123853%20AM.bmp.jpg"></div>
    <h1>Ray/ Sphere Intersection</h1>
    <h2>Point Light source and shading (ambient, diffuse, specular)</h2>
    <p>Given a ray <strong>p</strong>(t) = <strong>ro</strong> + t<strong>rd</strong>
      where <strong>ro</strong> is the origin of the ray and <strong>rd</strong>
      is its direction. A sphere with center <strong>c</strong> and radius R
      can be represented by the equation (<strong>p</strong> - <strong>c</strong>).(<strong>p</strong>
      - <strong>c</strong>) - R^2 = 0. Any point <strong>p</strong> satisfies
      this equation is on the sphere. If we plug points on the ray into this
      equation we get an equation in terms of t that is satisfied by the values
      of t that yield points on the sphere. </p>
    <p style="text-align: center;">(<strong>rd</strong> · <strong>rd</strong>)t^2
      + 2<strong>rd</strong> · (<strong>ro</strong> &#8722; <strong>c</strong>)t + (<strong>ro</strong>
      &#8722; <strong>c</strong>) · (<strong>e </strong>&#8722; <strong>c</strong>) &#8722; R^2
      = 0 (1)</p>
    <p style="text-align: left;">(1) is classic quadratic equation, it has the
      form At^2 + Bt + C = 0. The discriminant is B^2 &#8722; 4AC. If the discriminant
      is negative, its square root is imaginary and the line and sphere do not
      intersect. If the discriminant is positive, there are two solutions: one
      solution where the ray enters the sphere and one where it leaves. If the
      discriminant is zero, the ray grazes the sphere, touching it at exactly
      one point. [1]</p>
    <p style="text-align: left;">The normal vector at point <strong>p</strong>
      is given by the gradient <strong>n </strong>= 2(<strong>p</strong> &#8722; <strong>c</strong>).
      The unit normal is (<strong>p</strong> &#8722; <strong>c</strong>)/R. Normals
      allow us to calculate the direction of light that is reflected. In this
      project, I use Phong refection model as shown in the following figures
      [2]. The ambient term accounts for the scattered light present in the
      scene. This term is independent from any light source and it is the same
      for all fragments. The diffuse term corresponds to diffuse reflections.
      Usually a Lambertian model is used for this component. The specular term
      provides mirror-like reflections. Conceptually, the specular reflection
      will be at its maximum when we are looking at the object on an angle that
      is equal to the reflected light-direction vector. [2]</p>
    <div style="text-align: center;"><img title="[1]" alt="" src="Fullscreen%20capture%201242014%2012432%20PM.bmp.jpg"><br>
      <img alt="" src="Fullscreen%20capture%201242014%2013347%20PM.bmp.jpg"><br>
      <div style="text-align: left;">The following image is the result when I
        implement the discussed method. Light source is point light.</div>
    </div>
    <div style="text-align: center;"><img src="Fullscreen%20capture%201232014%20105659%20PM.bmp.jpg"><br>
    </div>
    <h1>Ray/ Cylinder Intersection</h1>
    <p>The infinite unit cylinder aligned along the z-axis is defined as: </p>
    <p style="text-align: center;">x^2 + y^2 = R^2&nbsp;</p>
    <p>To intersect a ray with this,&nbsp; &nbsp; &nbsp;&nbsp;&nbsp; &nbsp;
      &nbsp;&nbsp; </p>
    <p style="text-align: center;"> (<strong>ro</strong> + t<strong>rd</strong>)^2
      + (<strong>ro</strong> + t<strong>rd</strong>)^2 = R^2&nbsp; (2)</p>
    <p>(2) is classic quadratic equation, it has the form At^2 + Bt + C = 0. </p>
    <p><br>
      <br>
      The finite open-ended unit cylinder aligned along the z-axis is defined
      as: </p>
    <p>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp; x^2 + y^2 = R^2, zmin
      &lt; z &lt; zmax&nbsp;&nbsp; <br>
      <br>
      To handle this finite length cylinder, solve Equation 2 above. This gives,
      at most, two values of t. Call these t1 and t2. Calculate z1 and z2 using
      equations ( z1 = ro.z + t1rd.z and z2 = ro.z + t2rd.z) and then check zmin
      &lt; z1 &lt; zmax and zmin &lt; z2 &lt; zmax. Whichever intersection point
      passes this test and, if both pass the test, has the smallest non-negative
      value of t, is the closest intersection point of the ray with the
      open-ended finite cylinder.<br>
      We wish the finite length cylinder to be closed we must formulate an
      intersection calculation between the ray and the cylinder's end caps. The
      end caps have the formulate:</p>
    <p><br>
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; z = zmin&nbsp;&nbsp;&nbsp; &nbsp;
      &nbsp; &nbsp;&nbsp; x^2+y^2&nbsp; &lt;= R^2<br>
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; z = zmax&nbsp;&nbsp;&nbsp; &nbsp;
      &nbsp;&nbsp;&nbsp; x^2+y^2 &lt;= R^2<br>
      <br>
      Once you have calculated the solutions to Equation 2 you either know that
      there are no intersections with the infinite cylinder or you will know
      that there are one or two real intersection points (t1 and t2). The
      previous paragraph explained how to ascertain whether these correspond to
      points on the finite length open-ended cylinder. Now, if z1 and z2 lie
      either side of zmin we know that the ray intersects the zmin end cap, and
      can calculate the intersection point as:</p>
    <p><br>
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; t = (zmin - ro.z) / rd.z</p>
    <p><br>
      A similar equation holds for the zmax end cap.[3]</p>
    <p>The following image is the result when I implement the discussed method.</p>
    <div style="text-align: center;"><img alt="" src="Fullscreen%20capture%201232014%20110522%20PM.bmp.jpg"></div>
    <h1>Ray/Plane Intersection</h1>
    <p>Given a ray <strong>p</strong>(t) = <strong>ro</strong> + t<strong>rd</strong>
      where <strong>ro</strong> is the origin of the ray and <strong>rd</strong>
      is its direction. The equation for the plane is : </p>
    <p style="text-align: center;"><strong>p</strong> . <strong>n</strong> + d
      = 0 (3)</p>
    <p style="text-align: left;">Subtitude <strong>p</strong> into (3), we
      solve t as: </p>
    <p style="text-align: center;">t = - (ro . n + d) / (rd . n)</p>
    <p style="text-align: left;">The following image is the result when I
      implement the discussed method.</p>
    <div style="text-align: center;"><img alt="" src="Fullscreen%20capture%201232014%20110952%20PM.bmp.jpg"></div>
    <h1>Simple Shadow</h1>
    <p>The hard shadow is to test a ray from each point on the plane towards the
      light source. I also check if the ray intersects the object (e.g the
      sphere in the following figure) then at that point on the plane, the
      shadow is presented.</p>
    <div style="text-align: center;"><img alt="" src="Fullscreen%20capture%201242014%2015951%20PM.bmp.jpg"><br>
      <div style="text-align: left;">The following image is the result</div>
      <br>
      <div style="text-align: center;"><img alt="" src="Fullscreen%20capture%201232014%20111506%20PM.bmp.jpg"></div>
    </div>
    <h1>Reflection &amp; Animation of bouncing sphere</h1>
    <p>The directions of the reflected and refracted rays are given by the
      following formulas. For a ray with direction <b>rd</b>, and a surface
      with normal <b>N</b> (the <b>normal</b> is just the direction&nbsp;
      perpendicular to the surface - pointing directly away from it), the
      reflected ray direction <b>Rl</b> is given by
    </p>
    <p>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; c1 = -dot_product(
      N, rd )</p>
    <p>&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;
      &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; Rl = rd + (2 * N
      * c1 ) [5]<code></code></p>
    <h2><span style="color: red;">Video link: <a target="_blank" href="http://youtu.be/LSFHPoKcuP8">Bouncing
          ball</a></span></h2>
    <img alt="" src="Fullscreen%20capture%201232014%20114610%20PM.bmp.jpg"> <img

      alt="" src="../../../../Pictures/Picasa/Screen%20Captures/Fullscreen%20capture%201232014%20114610%20PM.bmp.jpg"><br>
    <h1>References</h1>
    <p><!--[if gte mso 9]><xml>
 <o:OfficeDocumentSettings>  <o:AllowPNG/> </o:OfficeDocumentSettings></xml><![endif]--></p>
    <p><!--[if gte mso 9]><xml>
 <w:WordDocument>  <w:View>Normal</w:View>  <w:Zoom>0</w:Zoom>  <w:TrackMoves/>  <w:TrackFormatting/>  <w:PunctuationKerning/>  <w:ValidateAgainstSchemas/>  <w:SaveIfXMLInvalid>false</w:SaveIfXMLInvalid>  <w:IgnoreMixedContent>false</w:IgnoreMixedContent>  <w:AlwaysShowPlaceholderText>false</w:AlwaysShowPlaceholderText>  <w:DoNotPromoteQF/>  <w:LidThemeOther>EN-US</w:LidThemeOther>  <w:LidThemeAsian>X-NONE</w:LidThemeAsian>  <w:LidThemeComplexScript>X-NONE</w:LidThemeComplexScript>  <w:Compatibility>   <w:BreakWrappedTables/>   <w:SnapToGridInCell/>   <w:WrapTextWithPunct/>   <w:UseAsianBreakRules/>   <w:DontGrowAutofit/>   <w:SplitPgBreakAndParaMark/>   <w:EnableOpenTypeKerning/>   <w:DontFlipMirrorIndents/>   <w:OverrideTableStyleHps/>  </w:Compatibility>  <m:mathPr>   <m:mathFont m:val="Cambria Math"/>   <m:brkBin m:val="before"/>   <m:brkBinSub m:val="&#45;-"/>   <m:smallFrac m:val="off"/>   <m:dispDef/>   <m:lMargin m:val="0"/>   <m:rMargin m:val="0"/>   <m:defJc m:val="centerGroup"/>   <m:wrapIndent m:val="1440"/>   <m:intLim m:val="subSup"/>   <m:naryLim m:val="undOvr"/>  </m:mathPr></w:WordDocument></xml><![endif]--><!--[if gte mso 9]><xml>
 <w:LatentStyles DefLockedState="false" DefUnhideWhenUsed="false"  DefSemiHidden="false" DefQFormat="false" DefPriority="99"  LatentStyleCount="371">  <w:LsdException Locked="false" Priority="0" QFormat="true" Name="Normal"/>  <w:LsdException Locked="false" Priority="9" QFormat="true" Name="heading 1"/>  <w:LsdException Locked="false" Priority="9" SemiHidden="true"   UnhideWhenUsed="true" QFormat="true" Name="heading 2"/>  <w:LsdException Locked="false" Priority="9" SemiHidden="true"   UnhideWhenUsed="true" QFormat="true" Name="heading 3"/>  <w:LsdException Locked="false" Priority="9" SemiHidden="true"   UnhideWhenUsed="true" QFormat="true" Name="heading 4"/>  <w:LsdException Locked="false" Priority="9" SemiHidden="true"   UnhideWhenUsed="true" QFormat="true" Name="heading 5"/>  <w:LsdException Locked="false" Priority="9" SemiHidden="true"   UnhideWhenUsed="true" QFormat="true" Name="heading 6"/>  <w:LsdException Locked="false" Priority="9" SemiHidden="true"   UnhideWhenUsed="true" QFormat="true" Name="heading 7"/>  <w:LsdException Locked="false" Priority="9" SemiHidden="true"   UnhideWhenUsed="true" QFormat="true" Name="heading 8"/>  <w:LsdException Locked="false" Priority="9" SemiHidden="true"   UnhideWhenUsed="true" QFormat="true" Name="heading 9"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="index 1"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="index 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="index 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="index 4"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="index 5"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="index 6"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="index 7"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="index 8"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="index 9"/>  <w:LsdException Locked="false" Priority="39" SemiHidden="true"   UnhideWhenUsed="true" Name="toc 1"/>  <w:LsdException Locked="false" Priority="39" SemiHidden="true"   UnhideWhenUsed="true" Name="toc 2"/>  <w:LsdException Locked="false" Priority="39" SemiHidden="true"   UnhideWhenUsed="true" Name="toc 3"/>  <w:LsdException Locked="false" Priority="39" SemiHidden="true"   UnhideWhenUsed="true" Name="toc 4"/>  <w:LsdException Locked="false" Priority="39" SemiHidden="true"   UnhideWhenUsed="true" Name="toc 5"/>  <w:LsdException Locked="false" Priority="39" SemiHidden="true"   UnhideWhenUsed="true" Name="toc 6"/>  <w:LsdException Locked="false" Priority="39" SemiHidden="true"   UnhideWhenUsed="true" Name="toc 7"/>  <w:LsdException Locked="false" Priority="39" SemiHidden="true"   UnhideWhenUsed="true" Name="toc 8"/>  <w:LsdException Locked="false" Priority="39" SemiHidden="true"   UnhideWhenUsed="true" Name="toc 9"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Normal Indent"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="footnote text"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="annotation text"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"
   Name="header"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="footer"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="index heading"/>  <w:LsdException Locked="false" Priority="35" SemiHidden="true"   UnhideWhenUsed="true" QFormat="true" Name="caption"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="table of figures"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="envelope address"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="envelope return"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="footnote reference"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="annotation reference"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="line number"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="page number"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="endnote reference"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="endnote text"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="table of authorities"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="macro"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="toa heading"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Bullet"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Number"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List 4"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List 5"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Bullet 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Bullet 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Bullet 4"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Bullet 5"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Number 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Number 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Number 4"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Number 5"/>  <w:LsdException Locked="false" Priority="10" QFormat="true" Name="Title"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Closing"/>
  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Signature"/>  <w:LsdException Locked="false" Priority="1" SemiHidden="true"   UnhideWhenUsed="true" Name="Default Paragraph Font"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Body Text"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Body Text Indent"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Continue"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Continue 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Continue 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Continue 4"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="List Continue 5"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Message Header"/>  <w:LsdException Locked="false" Priority="11" QFormat="true" Name="Subtitle"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Salutation"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Date"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Body Text First Indent"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Body Text First Indent 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Note Heading"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Body Text 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Body Text 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Body Text Indent 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Body Text Indent 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Block Text"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Hyperlink"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="FollowedHyperlink"/>  <w:LsdException Locked="false" Priority="22" QFormat="true" Name="Strong"/>  <w:LsdException Locked="false" Priority="20" QFormat="true" Name="Emphasis"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Document Map"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Plain Text"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="E-mail Signature"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="HTML Top of Form"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="HTML Bottom of Form"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Normal (Web)"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="HTML Acronym"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="HTML Address"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"
   Name="HTML Cite"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="HTML Code"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="HTML Definition"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="HTML Keyboard"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="HTML Preformatted"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="HTML Sample"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="HTML Typewriter"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="HTML Variable"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Normal Table"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="annotation subject"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="No List"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Outline List 1"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Outline List 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Outline List 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Simple 1"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Simple 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Simple 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Classic 1"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Classic 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Classic 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Classic 4"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Colorful 1"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Colorful 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Colorful 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Columns 1"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Columns 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Columns 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Columns 4"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Columns 5"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Grid 1"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Grid 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Grid 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"
   Name="Table Grid 4"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Grid 5"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Grid 6"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Grid 7"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Grid 8"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table List 1"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table List 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table List 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table List 4"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table List 5"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table List 6"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table List 7"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table List 8"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table 3D effects 1"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table 3D effects 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table 3D effects 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Contemporary"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Elegant"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Professional"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Subtle 1"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Subtle 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Web 1"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Web 2"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Web 3"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Balloon Text"/>  <w:LsdException Locked="false" Priority="39" Name="Table Grid"/>  <w:LsdException Locked="false" SemiHidden="true" UnhideWhenUsed="true"   Name="Table Theme"/>  <w:LsdException Locked="false" SemiHidden="true" Name="Placeholder Text"/>  <w:LsdException Locked="false" Priority="1" QFormat="true" Name="No Spacing"/>  <w:LsdException Locked="false" Priority="60" Name="Light Shading"/>  <w:LsdException Locked="false" Priority="61" Name="Light List"/>  <w:LsdException Locked="false" Priority="62" Name="Light Grid"/>  <w:LsdException Locked="false" Priority="63" Name="Medium Shading 1"/>  <w:LsdException Locked="false" Priority="64" Name="Medium Shading 2"/>  <w:LsdException Locked="false" Priority="65" Name="Medium List 1"/>  <w:LsdException Locked="false" Priority="66" Name="Medium List 2"/>  <w:LsdException Locked="false" Priority="67" Name="Medium Grid 1"/>  <w:LsdException Locked="false" Priority="68" Name="Medium Grid 2"/>  <w:LsdException Locked="false" Priority="69" Name="Medium Grid 3"/>
  <w:LsdException Locked="false" Priority="70" Name="Dark List"/>  <w:LsdException Locked="false" Priority="71" Name="Colorful Shading"/>  <w:LsdException Locked="false" Priority="72" Name="Colorful List"/>  <w:LsdException Locked="false" Priority="73" Name="Colorful Grid"/>  <w:LsdException Locked="false" Priority="60" Name="Light Shading Accent 1"/>  <w:LsdException Locked="false" Priority="61" Name="Light List Accent 1"/>  <w:LsdException Locked="false" Priority="62" Name="Light Grid Accent 1"/>  <w:LsdException Locked="false" Priority="63" Name="Medium Shading 1 Accent 1"/>  <w:LsdException Locked="false" Priority="64" Name="Medium Shading 2 Accent 1"/>  <w:LsdException Locked="false" Priority="65" Name="Medium List 1 Accent 1"/>  <w:LsdException Locked="false" SemiHidden="true" Name="Revision"/>  <w:LsdException Locked="false" Priority="34" QFormat="true"   Name="List Paragraph"/>  <w:LsdException Locked="false" Priority="29" QFormat="true" Name="Quote"/>  <w:LsdException Locked="false" Priority="30" QFormat="true"   Name="Intense Quote"/>  <w:LsdException Locked="false" Priority="66" Name="Medium List 2 Accent 1"/>  <w:LsdException Locked="false" Priority="67" Name="Medium Grid 1 Accent 1"/>  <w:LsdException Locked="false" Priority="68" Name="Medium Grid 2 Accent 1"/>  <w:LsdException Locked="false" Priority="69" Name="Medium Grid 3 Accent 1"/>  <w:LsdException Locked="false" Priority="70" Name="Dark List Accent 1"/>  <w:LsdException Locked="false" Priority="71" Name="Colorful Shading Accent 1"/>  <w:LsdException Locked="false" Priority="72" Name="Colorful List Accent 1"/>  <w:LsdException Locked="false" Priority="73" Name="Colorful Grid Accent 1"/>  <w:LsdException Locked="false" Priority="60" Name="Light Shading Accent 2"/>  <w:LsdException Locked="false" Priority="61" Name="Light List Accent 2"/>  <w:LsdException Locked="false" Priority="62" Name="Light Grid Accent 2"/>  <w:LsdException Locked="false" Priority="63" Name="Medium Shading 1 Accent 2"/>  <w:LsdException Locked="false" Priority="64" Name="Medium Shading 2 Accent 2"/>  <w:LsdException Locked="false" Priority="65" Name="Medium List 1 Accent 2"/>  <w:LsdException Locked="false" Priority="66" Name="Medium List 2 Accent 2"/>  <w:LsdException Locked="false" Priority="67" Name="Medium Grid 1 Accent 2"/>  <w:LsdException Locked="false" Priority="68" Name="Medium Grid 2 Accent 2"/>  <w:LsdException Locked="false" Priority="69" Name="Medium Grid 3 Accent 2"/>  <w:LsdException Locked="false" Priority="70" Name="Dark List Accent 2"/>  <w:LsdException Locked="false" Priority="71" Name="Colorful Shading Accent 2"/>  <w:LsdException Locked="false" Priority="72" Name="Colorful List Accent 2"/>  <w:LsdException Locked="false" Priority="73" Name="Colorful Grid Accent 2"/>  <w:LsdException Locked="false" Priority="60" Name="Light Shading Accent 3"/>  <w:LsdException Locked="false" Priority="61" Name="Light List Accent 3"/>  <w:LsdException Locked="false" Priority="62" Name="Light Grid Accent 3"/>  <w:LsdException Locked="false" Priority="63" Name="Medium Shading 1 Accent 3"/>  <w:LsdException Locked="false" Priority="64" Name="Medium Shading 2 Accent 3"/>  <w:LsdException Locked="false" Priority="65" Name="Medium List 1 Accent 3"/>  <w:LsdException Locked="false" Priority="66" Name="Medium List 2 Accent 3"/>  <w:LsdException Locked="false" Priority="67" Name="Medium Grid 1 Accent 3"/>  <w:LsdException Locked="false" Priority="68" Name="Medium Grid 2 Accent 3"/>  <w:LsdException Locked="false" Priority="69" Name="Medium Grid 3 Accent 3"/>  <w:LsdException Locked="false" Priority="70" Name="Dark List Accent 3"/>  <w:LsdException Locked="false" Priority="71" Name="Colorful Shading Accent 3"/>  <w:LsdException Locked="false" Priority="72" Name="Colorful List Accent 3"/>  <w:LsdException Locked="false" Priority="73" Name="Colorful Grid Accent 3"/>  <w:LsdException Locked="false" Priority="60" Name="Light Shading Accent 4"/>  <w:LsdException Locked="false" Priority="61" Name="Light List Accent 4"/>  <w:LsdException Locked="false" Priority="62" Name="Light Grid Accent 4"/>  <w:LsdException Locked="false" Priority="63" Name="Medium Shading 1 Accent 4"/>  <w:LsdException Locked="false" Priority="64" Name="Medium Shading 2 Accent 4"/>  <w:LsdException Locked="false" Priority="65" Name="Medium List 1 Accent 4"/>  <w:LsdException Locked="false" Priority="66" Name="Medium List 2 Accent 4"/>  <w:LsdException Locked="false" Priority="67" Name="Medium Grid 1 Accent 4"/>  <w:LsdException Locked="false" Priority="68" Name="Medium Grid 2 Accent 4"/>  <w:LsdException Locked="false" Priority="69" Name="Medium Grid 3 Accent 4"/>  <w:LsdException Locked="false" Priority="70" Name="Dark List Accent 4"/>  <w:LsdException Locked="false" Priority="71" Name="Colorful Shading Accent 4"/>
  <w:LsdException Locked="false" Priority="72" Name="Colorful List Accent 4"/>  <w:LsdException Locked="false" Priority="73" Name="Colorful Grid Accent 4"/>  <w:LsdException Locked="false" Priority="60" Name="Light Shading Accent 5"/>  <w:LsdException Locked="false" Priority="61" Name="Light List Accent 5"/>  <w:LsdException Locked="false" Priority="62" Name="Light Grid Accent 5"/>  <w:LsdException Locked="false" Priority="63" Name="Medium Shading 1 Accent 5"/>  <w:LsdException Locked="false" Priority="64" Name="Medium Shading 2 Accent 5"/>  <w:LsdException Locked="false" Priority="65" Name="Medium List 1 Accent 5"/>  <w:LsdException Locked="false" Priority="66" Name="Medium List 2 Accent 5"/>  <w:LsdException Locked="false" Priority="67" Name="Medium Grid 1 Accent 5"/>  <w:LsdException Locked="false" Priority="68" Name="Medium Grid 2 Accent 5"/>  <w:LsdException Locked="false" Priority="69" Name="Medium Grid 3 Accent 5"/>  <w:LsdException Locked="false" Priority="70" Name="Dark List Accent 5"/>  <w:LsdException Locked="false" Priority="71" Name="Colorful Shading Accent 5"/>  <w:LsdException Locked="false" Priority="72" Name="Colorful List Accent 5"/>  <w:LsdException Locked="false" Priority="73" Name="Colorful Grid Accent 5"/>  <w:LsdException Locked="false" Priority="60" Name="Light Shading Accent 6"/>  <w:LsdException Locked="false" Priority="61" Name="Light List Accent 6"/>  <w:LsdException Locked="false" Priority="62" Name="Light Grid Accent 6"/>  <w:LsdException Locked="false" Priority="63" Name="Medium Shading 1 Accent 6"/>  <w:LsdException Locked="false" Priority="64" Name="Medium Shading 2 Accent 6"/>  <w:LsdException Locked="false" Priority="65" Name="Medium List 1 Accent 6"/>  <w:LsdException Locked="false" Priority="66" Name="Medium List 2 Accent 6"/>  <w:LsdException Locked="false" Priority="67" Name="Medium Grid 1 Accent 6"/>  <w:LsdException Locked="false" Priority="68" Name="Medium Grid 2 Accent 6"/>  <w:LsdException Locked="false" Priority="69" Name="Medium Grid 3 Accent 6"/>  <w:LsdException Locked="false" Priority="70" Name="Dark List Accent 6"/>  <w:LsdException Locked="false" Priority="71" Name="Colorful Shading Accent 6"/>  <w:LsdException Locked="false" Priority="72" Name="Colorful List Accent 6"/>  <w:LsdException Locked="false" Priority="73" Name="Colorful Grid Accent 6"/>  <w:LsdException Locked="false" Priority="19" QFormat="true"   Name="Subtle Emphasis"/>  <w:LsdException Locked="false" Priority="21" QFormat="true"   Name="Intense Emphasis"/>  <w:LsdException Locked="false" Priority="31" QFormat="true"   Name="Subtle Reference"/>  <w:LsdException Locked="false" Priority="32" QFormat="true"   Name="Intense Reference"/>  <w:LsdException Locked="false" Priority="33" QFormat="true" Name="Book Title"/>  <w:LsdException Locked="false" Priority="37" SemiHidden="true"   UnhideWhenUsed="true" Name="Bibliography"/>  <w:LsdException Locked="false" Priority="39" SemiHidden="true"   UnhideWhenUsed="true" QFormat="true" Name="TOC Heading"/>  <w:LsdException Locked="false" Priority="41" Name="Plain Table 1"/>  <w:LsdException Locked="false" Priority="42" Name="Plain Table 2"/>  <w:LsdException Locked="false" Priority="43" Name="Plain Table 3"/>  <w:LsdException Locked="false" Priority="44" Name="Plain Table 4"/>  <w:LsdException Locked="false" Priority="45" Name="Plain Table 5"/>  <w:LsdException Locked="false" Priority="40" Name="Grid Table Light"/>  <w:LsdException Locked="false" Priority="46" Name="Grid Table 1 Light"/>  <w:LsdException Locked="false" Priority="47" Name="Grid Table 2"/>  <w:LsdException Locked="false" Priority="48" Name="Grid Table 3"/>  <w:LsdException Locked="false" Priority="49" Name="Grid Table 4"/>  <w:LsdException Locked="false" Priority="50" Name="Grid Table 5 Dark"/>  <w:LsdException Locked="false" Priority="51" Name="Grid Table 6 Colorful"/>  <w:LsdException Locked="false" Priority="52" Name="Grid Table 7 Colorful"/>  <w:LsdException Locked="false" Priority="46"   Name="Grid Table 1 Light Accent 1"/>  <w:LsdException Locked="false" Priority="47" Name="Grid Table 2 Accent 1"/>  <w:LsdException Locked="false" Priority="48" Name="Grid Table 3 Accent 1"/>  <w:LsdException Locked="false" Priority="49" Name="Grid Table 4 Accent 1"/>  <w:LsdException Locked="false" Priority="50" Name="Grid Table 5 Dark Accent 1"/>  <w:LsdException Locked="false" Priority="51"   Name="Grid Table 6 Colorful Accent 1"/>
  <w:LsdException Locked="false" Priority="52"   Name="Grid Table 7 Colorful Accent 1"/>  <w:LsdException Locked="false" Priority="46"   Name="Grid Table 1 Light Accent 2"/>  <w:LsdException Locked="false" Priority="47" Name="Grid Table 2 Accent 2"/>  <w:LsdException Locked="false" Priority="48" Name="Grid Table 3 Accent 2"/>  <w:LsdException Locked="false" Priority="49" Name="Grid Table 4 Accent 2"/>  <w:LsdException Locked="false" Priority="50" Name="Grid Table 5 Dark Accent 2"/>  <w:LsdException Locked="false" Priority="51"   Name="Grid Table 6 Colorful Accent 2"/>  <w:LsdException Locked="false" Priority="52"   Name="Grid Table 7 Colorful Accent 2"/>  <w:LsdException Locked="false" Priority="46"   Name="Grid Table 1 Light Accent 3"/>  <w:LsdException Locked="false" Priority="47" Name="Grid Table 2 Accent 3"/>  <w:LsdException Locked="false" Priority="48" Name="Grid Table 3 Accent 3"/>  <w:LsdException Locked="false" Priority="49" Name="Grid Table 4 Accent 3"/>  <w:LsdException Locked="false" Priority="50" Name="Grid Table 5 Dark Accent 3"/>  <w:LsdException Locked="false" Priority="51"   Name="Grid Table 6 Colorful Accent 3"/>  <w:LsdException Locked="false" Priority="52"   Name="Grid Table 7 Colorful Accent 3"/>  <w:LsdException Locked="false" Priority="46"   Name="Grid Table 1 Light Accent 4"/>  <w:LsdException Locked="false" Priority="47" Name="Grid Table 2 Accent 4"/>  <w:LsdException Locked="false" Priority="48" Name="Grid Table 3 Accent 4"/>  <w:LsdException Locked="false" Priority="49" Name="Grid Table 4 Accent 4"/>  <w:LsdException Locked="false" Priority="50" Name="Grid Table 5 Dark Accent 4"/>  <w:LsdException Locked="false" Priority="51"   Name="Grid Table 6 Colorful Accent 4"/>  <w:LsdException Locked="false" Priority="52"   Name="Grid Table 7 Colorful Accent 4"/>  <w:LsdException Locked="false" Priority="46"   Name="Grid Table 1 Light Accent 5"/>  <w:LsdException Locked="false" Priority="47" Name="Grid Table 2 Accent 5"/>  <w:LsdException Locked="false" Priority="48" Name="Grid Table 3 Accent 5"/>  <w:LsdException Locked="false" Priority="49" Name="Grid Table 4 Accent 5"/>  <w:LsdException Locked="false" Priority="50" Name="Grid Table 5 Dark Accent 5"/>  <w:LsdException Locked="false" Priority="51"   Name="Grid Table 6 Colorful Accent 5"/>  <w:LsdException Locked="false" Priority="52"   Name="Grid Table 7 Colorful Accent 5"/>  <w:LsdException Locked="false" Priority="46"   Name="Grid Table 1 Light Accent 6"/>  <w:LsdException Locked="false" Priority="47" Name="Grid Table 2 Accent 6"/>  <w:LsdException Locked="false" Priority="48" Name="Grid Table 3 Accent 6"/>  <w:LsdException Locked="false" Priority="49" Name="Grid Table 4 Accent 6"/>  <w:LsdException Locked="false" Priority="50" Name="Grid Table 5 Dark Accent 6"/>  <w:LsdException Locked="false" Priority="51"   Name="Grid Table 6 Colorful Accent 6"/>  <w:LsdException Locked="false" Priority="52"   Name="Grid Table 7 Colorful Accent 6"/>  <w:LsdException Locked="false" Priority="46" Name="List Table 1 Light"/>  <w:LsdException Locked="false" Priority="47" Name="List Table 2"/>  <w:LsdException Locked="false" Priority="48" Name="List Table 3"/>  <w:LsdException Locked="false" Priority="49" Name="List Table 4"/>  <w:LsdException Locked="false" Priority="50" Name="List Table 5 Dark"/>  <w:LsdException Locked="false" Priority="51" Name="List Table 6 Colorful"/>  <w:LsdException Locked="false" Priority="52" Name="List Table 7 Colorful"/>  <w:LsdException Locked="false" Priority="46"   Name="List Table 1 Light Accent 1"/>  <w:LsdException Locked="false" Priority="47" Name="List Table 2 Accent 1"/>  <w:LsdException Locked="false" Priority="48" Name="List Table 3 Accent 1"/>  <w:LsdException Locked="false" Priority="49" Name="List Table 4 Accent 1"/>
  <w:LsdException Locked="false" Priority="50" Name="List Table 5 Dark Accent 1"/>  <w:LsdException Locked="false" Priority="51"   Name="List Table 6 Colorful Accent 1"/>  <w:LsdException Locked="false" Priority="52"   Name="List Table 7 Colorful Accent 1"/>  <w:LsdException Locked="false" Priority="46"   Name="List Table 1 Light Accent 2"/>  <w:LsdException Locked="false" Priority="47" Name="List Table 2 Accent 2"/>  <w:LsdException Locked="false" Priority="48" Name="List Table 3 Accent 2"/>  <w:LsdException Locked="false" Priority="49" Name="List Table 4 Accent 2"/>  <w:LsdException Locked="false" Priority="50" Name="List Table 5 Dark Accent 2"/>  <w:LsdException Locked="false" Priority="51"   Name="List Table 6 Colorful Accent 2"/>  <w:LsdException Locked="false" Priority="52"   Name="List Table 7 Colorful Accent 2"/>  <w:LsdException Locked="false" Priority="46"   Name="List Table 1 Light Accent 3"/>  <w:LsdException Locked="false" Priority="47" Name="List Table 2 Accent 3"/>  <w:LsdException Locked="false" Priority="48" Name="List Table 3 Accent 3"/>  <w:LsdException Locked="false" Priority="49" Name="List Table 4 Accent 3"/>  <w:LsdException Locked="false" Priority="50" Name="List Table 5 Dark Accent 3"/>  <w:LsdException Locked="false" Priority="51"   Name="List Table 6 Colorful Accent 3"/>  <w:LsdException Locked="false" Priority="52"   Name="List Table 7 Colorful Accent 3"/>  <w:LsdException Locked="false" Priority="46"   Name="List Table 1 Light Accent 4"/>  <w:LsdException Locked="false" Priority="47" Name="List Table 2 Accent 4"/>  <w:LsdException Locked="false" Priority="48" Name="List Table 3 Accent 4"/>  <w:LsdException Locked="false" Priority="49" Name="List Table 4 Accent 4"/>  <w:LsdException Locked="false" Priority="50" Name="List Table 5 Dark Accent 4"/>  <w:LsdException Locked="false" Priority="51"   Name="List Table 6 Colorful Accent 4"/>  <w:LsdException Locked="false" Priority="52"   Name="List Table 7 Colorful Accent 4"/>  <w:LsdException Locked="false" Priority="46"   Name="List Table 1 Light Accent 5"/>  <w:LsdException Locked="false" Priority="47" Name="List Table 2 Accent 5"/>  <w:LsdException Locked="false" Priority="48" Name="List Table 3 Accent 5"/>  <w:LsdException Locked="false" Priority="49" Name="List Table 4 Accent 5"/>  <w:LsdException Locked="false" Priority="50" Name="List Table 5 Dark Accent 5"/>  <w:LsdException Locked="false" Priority="51"   Name="List Table 6 Colorful Accent 5"/>  <w:LsdException Locked="false" Priority="52"   Name="List Table 7 Colorful Accent 5"/>  <w:LsdException Locked="false" Priority="46"   Name="List Table 1 Light Accent 6"/>  <w:LsdException Locked="false" Priority="47" Name="List Table 2 Accent 6"/>  <w:LsdException Locked="false" Priority="48" Name="List Table 3 Accent 6"/>  <w:LsdException Locked="false" Priority="49" Name="List Table 4 Accent 6"/>  <w:LsdException Locked="false" Priority="50" Name="List Table 5 Dark Accent 6"/>  <w:LsdException Locked="false" Priority="51"   Name="List Table 6 Colorful Accent 6"/>  <w:LsdException Locked="false" Priority="52"   Name="List Table 7 Colorful Accent 6"/> </w:LatentStyles></xml><![endif]--><!--[if gte mso 10]>
<style> /* Style Definitions */ table.MsoNormalTable	{mso-style-name:"Table Normal";	mso-tstyle-rowband-size:0;	mso-tstyle-colband-size:0;	mso-style-noshow:yes;	mso-style-priority:99;	mso-style-parent:"";	mso-padding-alt:0in 5.4pt 0in 5.4pt;	mso-para-margin-top:0in;	mso-para-margin-right:0in;	mso-para-margin-bottom:8.0pt;	mso-para-margin-left:0in;	line-height:107%;	mso-pagination:widow-orphan;	font-size:11.0pt;	font-family:"Calibri",sans-serif;	mso-ascii-font-family:Calibri;	mso-ascii-theme-font:minor-latin;	mso-hansi-font-family:Calibri;	mso-hansi-theme-font:minor-latin;}</style><![endif]-->
    </p>
    <p class="MsoNormal" style="line-height:normal"><br>
      <span style="font-size:12.0pt;
font-family:&quot;Times New Roman&quot;,serif">[1] P. Shirley et al. Fundamental
        of Computer Graphics. </span>A K Peters/CRC Press; 3 edition, July 21,
      2009.</p>
    <p class="MsoNormal" style="line-height:normal"><span style="font-size:12.0pt;
font-family:&quot;Times New Roman&quot;,serif">[2] D. Cantor et. al. WebGL
        Beginner's Guide. </span>Packt Publishing, June 15, 2012.</p>
    <p class="MsoNormal" style="line-height:normal"><span style="font-size:12.0pt;
font-family:&quot;Times New Roman&quot;,serif">[3] Ray- Cylinder Intersection,
        https://www.cl.cam.ac.uk/teaching/1999/AGraphHCI/SMAG/node2.html#SECTION00023200000000000000,
        accessed Dec 01, 2014</span></p>
    <p class="MsoNormal" style="line-height:normal"><span style="font-size:12.0pt;
font-family:&quot;Times New Roman&quot;,serif">[4] Ray-Plane intersection,
http://www.cs.princeton.edu/courses/archive/fall00/cs426/lectures/raycast/sld017.htm,
      </span><span style="font-size:12.0pt;
font-family:&quot;Times New Roman&quot;,serif">accessed Dec 03, 2014.</span></p>
    <p class="MsoNormal" style="line-height:normal"><span style="font-size:12.0pt;
font-family:&quot;Times New Roman&quot;,serif">[5] Reflection,
        https://www.cs.unc.edu/~rademach/xroads-RT/RTarticle.html, accessed Dec
        03, 2014</span></p>
    <p class="MsoNormal" style="line-height:normal"><span style="font-size:12.0pt;
font-family:&quot;Times New Roman&quot;,serif">[6] K. Matsuda, R. Lea. WebGL
        Programming Guide: Interactive 3D Graphics Programming with WebGL.
        Addison-Wesley, Jul 4, 2013.</span></p>
    <p></p>
    <br>
    <br>
    <p><br>
    </p>
    <p><br>
    </p>
  </body>
</html>
```
