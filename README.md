
public static Bitmap drawStar(int W, int H, int color, boolean andRing)
{
    Path path = new Path();
    Bitmap output = Bitmap.createBitmap(W, H, Config.ARGB_8888);
    Canvas canvas = new Canvas(output);
    final Paint paint = new Paint(Paint.ANTI_ALIAS_FLAG);
    paint.setColor(color);

    float midW ,min ,fat ,half ,radius;

    if(andRing)
    {
        midW = W / 2;
        min = Math.min(W, H);
        half = min / 2;
        midW = midW - half;

        fat = min / 17;
        radius = half - fat;

        paint.setStrokeWidth(fat);
        paint.setStyle(Paint.Style.STROKE);
        canvas.drawCircle(midW + half, half, radius, paint);

        path.reset();
        paint.setStyle(Paint.Style.FILL);
        path.moveTo( half * 0.5f, half * 0.84f);
        path.lineTo( half * 1.5f, half * 0.84f);
        path.lineTo( half * 0.68f, half * 1.45f);
        path.lineTo( half * 1.0f, half * 0.5f);
        path.lineTo( half * 1.32f, half * 1.45f);
        path.lineTo( half * 0.5f, half * 0.84f);
    }
    else
    {
        min = Math.min(W, H);
        half = min/2;

        path.reset();
        paint.setStyle(Paint.Style.FILL);

        path.moveTo( half * 0.1f  , half * 0.65f);
        path.lineTo( half * 1.9f  , half * 0.65f);
        path.lineTo( half * 0.40f , half * 1.65f);
        path.lineTo( half       , 0           );
        path.lineTo( half * 1.60f, half * 1.65f);
        path.lineTo( half * 0.1f, half * 0.65f);
    }

    canvas.drawPath(path, paint);

    return output;
}
