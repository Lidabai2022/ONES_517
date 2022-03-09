# ONES_517

包 com.neo.controller；

导入 com.neo.entity.Visitor；
导入 com.neo.repository.VisitorRepository；
导入 org.springframework.beans.factory.annotation.Autowired；
导入 org.springframework.web.bind.annotation.RequestMapping；
导入 org.springframework.web.bind.annotation.RestController；

导入 javax.servlet.http.HttpServletRequest；

@RestController
公共 类 访客控制器{

    @自动连线
    私人 访客存储库；
	
    @RequestMapping ( " / " )
    公共 字符串 索引（HttpServletRequest 请求）{
        字符串ip =请求。获取远程地址（）；
        访客访客=存储库。findByIp(ip);
        如果（访问者==空）{
            访客=新 访客（）；
            访客。设置IP（IP）；
            访客。设置时间（1）；
        }其他{
            访客。setTimes(访问者。getTimes () + 1 );
        }
        存储库。保存（访客）；
        返回 “我见过ip ” +访问者。getIp() + "  " +访客。getTimes() + "次。" ;
    }
}
