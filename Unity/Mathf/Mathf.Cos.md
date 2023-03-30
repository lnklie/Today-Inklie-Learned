Mathf.Cos에 대하여
=====
개념
---
- Cosine을 구하는 메소드
- Cosine이란(https://github.com/lnklie/Today-Inklie-Learned/blob/main/Math/Cosine.md)

활용
---
```c#
... HTC_1_1.Movement_2_3D Parabolic Movement
        // Extract the X  Y componenent of the velocity
        float Vx = Mathf.Sqrt(projectile_Velocity) * Mathf.Cos(firingAngle * Mathf.Deg2Rad);
        float Vy = Mathf.Sqrt(projectile_Velocity) * Mathf.Sin(firingAngle * Mathf.Deg2Rad);
...
```