---
title: Overview of Assurance Process
toc: True
sidebar: overview_sidebar
permalink: assurance_overview.html
summary: "Overview of the assurance processes involved in developing and deploying a solution"
---
{% include note-notpublished.html %}

The assurance process that has been adopted for the UEC Appointment Booking standard is based on the following principles:

## Assurance principles 
High-level design principles related to the assurance processes 
* assurance should be lightweight but appropriate 
* testing should be automated where possible to establish technical conformance 
* a level of self-certified solution assurance will be made available to organisations deploying the APIs 
* all artefacts related to assurance and testing should be made available as part of the ecosystem (public domain) prior to engaging in a formal NHS Digital assurance process 
* a set of evidence based around self-assurance activities will speed up the assurance process 

The assurance process is illustrated in the following interactive diagram. For detail on each stage please click on the relevent step:

<div class="mxgraph" style="max-width:100%;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;target&quot;:&quot;blank&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;xml&quot;:&quot;&lt;mxfile modified=\&quot;2019-04-18T11:29:56.933Z\&quot; host=\&quot;www.draw.io\&quot; agent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/8.8.0 Chrome/61.0.3163.100 Electron/2.0.2 Safari/537.36\&quot; etag=\&quot;b4pF9wqjslOH4kPessls\&quot; version=\&quot;10.6.3\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;PTt-hyj0bQr8gjIvqhx4\&quot; name=\&quot;Page-1\&quot;&gt;7V1td5rKFv41+YgLGBjgo9GY9jRtc09ue9v7xYUwKg0yHMDE9NefGV4UZkYlCaJi27WiDMPbPM9+mc3e4xUYLFa3kR3OP2MX+Veq7K6uwPBKVRXT1MkHbXnJWyxVzlpmkefmbZuGB+83yhuLbkvPRXGlY4Kxn3hhtdHBQYCcpNJmRxF+rnabYr961dCeIa7hwbF9vvV/npvM81YFWpsdH5A3m+eXNlUj27Gwi875k8Rz28XPpSZwcwUGEcZJ9m2xGiCfjl4xLtlxoy17PeMLsnEfDf7j/KX4H4JvY0eTAMiu9WT7y/wBrm3ncRbhZeDmt5G8FM/mY+cR0dMpV+C6eJwIBcnbr69x1+eumt7L+rLPcy9BD6Ht0L3PhESkbZ4s/Hx3iCJvgRIU0S5eMCPNMmkmaCe2F6Ao37YjJ6cOIFtTz/cH2MdRekGgwv5wNCDtcRLhR1TaAx0TTabCh989vChK0KpEkHyIbhEmNxu9kC753gL8l+rmc4lKwMob5yUaGXreaOf8na1PvcGEfMlheQVEqsVB9LCcSPcRdlAct8ERuWGOMHADYPSvZQ7uAAfk8OuZb8dxzpopYVHpwGn6rz4b1iNZmw1QqdJBkXWOD4YpoIMCzffTwfxo/Ajuv/3/C775/uHh9tbCq1+SymuMKxX6ST48qWYtRgj+s6TK6nozVqWmEnxFIz2BFKdy2ScdVC1clY+AM/r5gP1l4uGAUE/ux/EysgOCc34L5JGyu8j6cjwh455UySAEvcyQvMn2vVlANh2CMVUj1xRFj+j9fr5j4bkuvYyQfRt+yofkiwn1qvoAJscX1RDwRW1Ae0z+DuSFdr1aziL129D82jc+/ZCMy5VdRpObvOgqikiVK0XP94ChcOP+mdg/0jIg40Af9fB6W98PPXKJ75Rv4iiZ4xkObP9m08oIzqbPHcZhfrO/UJK85NbcXia4ShgUuH3q1m1YQVpGHh24IU8cwoxR+m+9p3DiNOGw5MMc42XkoF30yfoldjRDOx2GrB8dl50ci5BvJ95T1eds3vTXQND3iWe9Te2VcLDjMHO3p96K4imW2K0jXF/uLMZk6iondyKLaR7MfzI7JwcEnOjlR35guvGTbvT0YnO4Ku8cvmy1e3XlB9SUH6VxAcoPvcde6tzkJNM1rcoyS62eIrvT/CiGQevbeDupRE7YyUsmMJlBO7ZoKjW8kzMTzbeLmFJbxuBJGSnlLGUBGsZpyYJaY5Z9ObIA68qCdVqyAM9RFixDOS1ZAH/sAk/x/XOXE7MLfNzyDGRBUZkQTpvC8Nf8x9Dyv/+Owp8Pyufv7sj4uJS6N32pJQvCsRCIgrCfcVKSAM7SKnCSoGvtSYIw9H2hVmEXw8uSIByzo9mEXXd9XoLAukdEDnp8LLlVSahjWjsiCYeOJLETQd20ekz8PxNGLpbEnUqDYN+pmgtL7ZL285IvDoHjy5fCv775I2BvFDA26qhb8lsFTDHWh24/2YFFrI47fnIiBkxGM52AiNWJd53cQG40+lFGUji9EDGy1YSQZRj6HorOPQfk9TMkNjuoCIWXmKAdKNlDHHJRW6OCAkVUuFmF5PwoNRr/LL0ILcjo0kQhm2YzkrOSTzty44ujCpCtvVRRQatcEaWHtMmVIYopEiq5fXmy9Hx3QxPkT+ncFsXJxREFyuqpEaU9+yImygAvQh/RlEPSBVNmPAz6dxfHjE2y2slQQ5Dl1i41PhJkZpGdc4MqDJpyfmnMMC14PGII43zH9kP+i5x5QAG5ShMupzhaZFnKskORmpJdCd3y4nhJkLg0wiiKoTLzGCgI7rfLmRoxzXhuh/Srt0iLgMpIsAOa0BDLuvXOniD/HsdeqinAcIKTBC9IB5/u2FTciBKU04v1iwmmLJpt5vcznCcJrXLq04FQR44bKD3PIfTzCHxRzyFXVEeundjkg7bHtJOXvEjIzxxlaea/hHOJgDcCdDQHlZ3hcuJ7jpTg50Ca2o7nk6dBpNmOHvtRMsHEsR4rMiCzALMXUjXYAE9UhZ3v6rxu0S2eJkVb4zSpFTfoSGhuf1qmIE9ml3AdOtanqJrBEsZUq2epHexT4N5zNRfrE3Pt2P7NICuSzNwbexahVBXQ8xEtd4GGy5JZq6Uc2WoJp9G82coKSekouHY8Xw/JaxAhxNI0S087+4w94+DZavDEdpKDGS8T3wvQYF2km+q03PwuVjNaPNx7Qshe9Dx6yDTFvRHfRGYSM6ElCLBqWs/kUd60Nu/R1ngjdHbuibbXPQl9+wVFtHo3wmSMdDJKDlVGo/svt+RvTBRw0pCzoRaJVgXwBuRgByoPetHWPOQ1EpvPDnJ5L+Q+8YRiWuAwAhSB0Y8BdlGDTiW0qu+iFAhFAi4S74MJd40q+L3A7YWeU7J1VL4sX9+MVIHytX8vI9R7RhNyJ2g8QwGKPKehYLXFBKsNfm6oC4zs5lVY8whdvJmlU5CFnSB3XIS5mvGoTAZryFcst29sa+SxnKY8kt5orDbkCa1fGa+xEbxfXM+RKrPvgwX2amTwCUldkcemxKcs1ywczzHolYN9HJK6amkDOiEnB7ge2lSnN5lCa7JxNl03RNZOhCF8P4bCzIvLdGtQHKOgCKzR83q2L+HplPRvxq+xLJ3FGrbnwYpzbFQB1MeKw4cRCi8uYMG+zoXA4ihxsICFmBMi29omJ66XMbEOdOWiy6QEYLKGYJEidDxKiIx6m5S4xZJPg86XRoXTY0KN7NYu+garEAUxiqWnWPIC0gVRR4EM8mg8jlH05Dl0hm1HZOqV27PxwqZxz4C+VW4yNmJUZ2O6BgTeYpEvX1l/zjgQJWoGPpuZeesy/X+AmbdwTsJPAJlJBHEPCfS9JeFA3CPn9MdZ1zFhWpA0owM0mctp1zXRFAEKpggNhFvEoIscx3PXA+pePeDhWDKkYotOokekuxfPx1PfnjX5Yl1mIRfFQIuAeAXyBuYKwoXizrXkxTWsibzZU36vzigXMteDzs4Qafl9u3CQBEu0iAczN9Dtl13uuu02Si3KiLx6/F8x2a6WZIJiHdsWajDEgNcZ4kuXnkIq9ouPelLi02apUkvyA7Sqo3l8ATrT1SrbFSC1rgBppyVANdzJMxMgKFdzro8vQGe6Oka7AqTVFaCjrZux8747JEAmrJaFH1+AznRRjR0CtFkndrM07M+r8sqw4nViDyB4gkTlnRHIg2cqK5BNbdcsrXqWLdnFBB77pdQtpB3inZdSKxfSZWY1b+YAoxgEcX/yJbuFt+Y670SoQypGUL5wdC1TJ5x6Zlrm1Qi2vqSPwSQqvXlBH/ZEzdUfiMlSx2/+Q5Zml6d5K1kUQ26LLJ8/DWZfwzsI/MQaP8X+p0X8KB27VuXG92behFalpcYxreQPIySlK0HQJNWzXPWBszYCkm5/t8OuFqMpfJR/ndXXdAKfkCUijdIqS1Je0Ddq5OPLhwfyd0h4k6QpQg/Zu1by7d52HlPZfvLQ88Xxhv0NDQ0IEgNkhadNE4kBQtq096NTYtrc4SyJ7Kx/cOpdnNA1eGKcEMUk2lcl3zJVQlPJ7GIliAujhimzmacaENRFtkqOY68u9JCuLSTjQKJ5H9SPLBueUinthXFFkSGbbwKKisujkaVG6KHjKUYOJjYtTOLeAqEkHldWT2sId+aNucbX+eiiFCNwIMwvc7mPuf2cf0vrEKBlAU1PM44kQ5Vc7CyztT4qqUbvAh5A5kWVzvsNh0o0Es9Ta7xNPzvka+SYktYFihwkpZUoCS0/ofV8Ef2yXvFlvZCLqjXIAagwHND4QjIo4AA8GAe6WE3fTA3S+7S8ojG2HfLSfqgSJDHSNUKYb7ftJ2XDszTh9C/vdqiyoV6bDfn7THwbGAKQBUEl0EC6sBjkLpYU7k8Xntix50hLb7NEF9WzI4WmYowcHEXkSg1qcUuuRoWAoFwECFw40EAh6d3fziox+tD6DR/7xs/hp5H6QRBxpusxRraThuNZAvCPW3mrSefxXye/KDiqnEJbPoxI5WO27aIFHuMnGilEz72URWmPnXeqlgY2fzLhD2DLW6ZhW34AO9dCNRcb3zmG9TNf9SoLFJVnwbqt8rPWyuunb2SzhEujOIkViXYsoPZI5nbstgLFvA5SBNJ6vjjp3cEJwC4DBbsDFNT1DgNldAcoRdW6jJTZHaQYGwU65UtY3cEJgA4Dld13N4DSrS4DpXQHKFPvMlBHm+8ewJlQ2LBHp5ACHUKKdfv0TiHVodAEG0PSBblE5wtUh2IT7JS3WxLVodgEG0TqlkR1KDbBJum3jBNpijBOSt1v6SvEz9iliN38Cw==&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>


## Supplier

### Explore requirements and standards

  Explore published documentation covering detailed technical and business requirements available on NHS Developer portal

### Design, build and self test

  Using published documentation, gaining access to NHS Digital integration test environments design, build and self test solution

### Integration testing

  Technical confirmance with Solutions ASsurance (SA) team. Undertaking testing and validation activities against a services requirements. 
  Providing evidence where applicable. Completing the <a href="assurance_scal.html" target="_blank">Supplier Conformance Assessment List</a>

### Completion of SCAL

  qwerty

### Technical conformance certificate

  qwerty

### Connection agreement

  qwerty

## Service provider/comissioner

### Elegibility and prerequisites

  qwerty
  
### End user NHS Digital service pack

  qwerty

### Local Assurance

  qwerty
  
### End user preparation

  qwerty
  
### On-line end user agreement

  qwerty
  
## Service provider and supplier

## Testing Assets 
TBC - Details of POC? 

## Test Environments 
TBC - Details of POC?
