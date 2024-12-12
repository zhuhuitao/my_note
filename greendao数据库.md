### GrenDao数据库升级

1，修改gradle数据库版本
```
    greendao {
        schemaVersion 10//数据库版本号 每次升级数据库都需要改变版本，只能增加
        daoPackage 'com.atoto.module.main.greendao.gen'  //设置DaoMaster、DaoSession、Dao包名
        targetGenDir 'src/main/java' //设置DaoMaster、DaoSession、Dao目录
    }
    ```

2，创建GreenDaoUpdateHelper 继承 DaoMaster.OpenHelper
```
public class GreenDaoUpdateHelper extends DaoMaster.OpenHelper {
    public GreenDaoUpdateHelper(Context context, String name) {
        super(context, name);
    }

    public GreenDaoUpdateHelper(Context context, String name, SQLiteDatabase.CursorFactory factory) {
        super(context, name, factory);
    }

    @Override
    public void onUpgrade(Database db, int oldVersion, int newVersion) {
        //数据库版本小于9的时候，直接删除所有表，然后重新创建
        //后续更新数据库时要保数据更新
        if (oldVersion < 9) {
            dropAllTabs(db);
        } else if (oldVersion == 9) {
            addBefExeColumn(db);
        } else {
            throw new UnsupportedOperationException("Migration not supported yet");
        }
    }

    private void dropAllTabs(Database db) {
        DaoMaster.dropAllTables(db, true);
        DaoMaster.createAllTables(db, false);
    }

    //当版本升级到10的时候，COMMAND_CACHE_LIST_BEAN 增加 CONTENT_TEXT
    private void addBefExeColumn(Database db) {
        db.execSQL("ALTER TABLE 'COMMAND_CACHE_LIST_BEAN' ADD COLUMN 'CONTENT_TEXT' TEXT ");
    }

}
```