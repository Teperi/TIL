# CSS Media query

- 2019.04.18: 첫 작성

## Media query

- 화면의 종류와 크기에 따라 디자인을 다르게 줄 수 있음
  - 반응형 디자인의 핵심
- 작은 화면이 높은 우선순위를 가질 수 있도록 작은 설정을 CSS 의 아래쪽에 배치
- 모바일에서 적용시키기 위해 meta tag 를 넣어주어야 함

  - _예제: Holy grail layout 적용_

  ```HTML
  <!doctype>
  <html>
  <head>
      <meta charset="utf-8">
      <style>
          .container{
              display: flex;
              flex-direction: column;
          }
          header{
              border-bottom:1px solid gray;
              padding-left:20px;
          }
          footer{
              border-top:1px solid gray;
              padding:20px;
              text-align: center;
          }
          .content{
              display:flex;
          }
          .content nav{
              border-right:1px solid gray;
          }
          .content aside{
              border-left:1px solid gray;
          }
          @media(max-width:500px){
              .content{
                  flex-direction: column;
              }
              .content nav, .content aside{
                  border:none;
                  flex-basis: auto;
              }
              main{
                  order:0;
              }
              nav{
                  order:1;
              }
              aside{
                  order:2;
                  display: none;
              }
          }
          nav, aside{
              flex-basis: 150px;
              flex-shrink: 0;
          }
          main{
              padding:10px;
          }
      </style>
  </head>
  <body>
      <div class="container">
          <header>
              <h1>생활코딩</h1>
          </header>
          <section class="content">
              <nav>
                  <ul>
                      <li>html</li>
                      <li>css</li>
                      <li>javascript</li>
                  </ul>
              </nav>
              <main>
                  Lorem ipsum dolor sit amet, consectetur adipisicing elit. Reiciendis veniam totam labore ipsum, nesciunt temporibus repudiandae facilis earum, sunt autem illum quam dolore, quae optio nemo vero quidem animi tempore aliquam voluptas assumenda ipsa voluptates. Illum facere dolor eos, corporis nobis, accusamus velit, similique cum iste unde vero harum voluptatem molestias excepturi. Laborum beatae, aliquid aliquam excepturi pariatur soluta asperiores laudantium iste, architecto ducimus fugiat sed, saepe quaerat recusandae exercitationem sapiente, impedit nostrum error. Doloremque impedit, eos in quos assumenda illo eum dicta. Voluptatum quaerat excepturi consectetur, doloremque esse deleniti commodi natus, maxime sit? Officia rerum quibusdam porro dolorum numquam harum soluta ex quo! Vero, nam? Necessitatibus rem hic perferendis maiores obcaecati voluptate sunt autem id doloribus, similique repudiandae nesciunt vel facere ex accusantium ipsum provident iste itaque? Perferendis culpa nostrum repellendus dolores repudiandae assumenda, tempora laudantium in quibusdam placeat facilis ex voluptatem provident velit iusto fuga eum nobis deserunt enim minus. Explicabo vel labore, eum doloremque, impedit recusandae aut illum corporis quis atque sit vero quasi tempore placeat ipsam similique quo delectus provident animi distinctio debitis eligendi voluptatum! Dolorem perspiciatis similique non fugit eaque? Commodi suscipit earum aliquam rem, neque ad. Obcaecati nisi beatae officia inventore laborum nostrum natus perspiciatis iste, aperiam vero quisquam saepe labore facilis veritatis illo excepturi vitae autem quis! Voluptatibus atque doloribus perferendis, eligendi ex aliquid debitis laudantium omnis accusamus similique cum mollitia quos adipisci reprehenderit assumenda sequi, dolore tenetur ipsam, odio, vero reiciendis iure. Dolore itaque nesciunt ipsam, id maxime saepe officiis dolorum molestias earum temporibus? Possimus ipsum accusamus quasi minima, quod magnam iusto non cupiditate facilis pariatur aliquam omnis, blanditiis assumenda magni ad voluptas dicta est optio reprehenderit rem ratione earum ipsa, dolor vero! Totam, adipisci eos nihil repellendus. Maiores, blanditiis. Officiis aspernatur iure culpa illo sint ex id perferendis, explicabo architecto ipsa voluptatibus nesciunt pariatur commodi cum quam. Obcaecati ut quidem quam error nemo. Pariatur aliquid autem inventore laboriosam, velit totam, temporibus ad magnam minus, quis nesciunt aperiam veritatis. Vitae porro provident magni eos sit sed dignissimos iure natus odio nostrum molestiae atque mollitia saepe adipisci ut velit quo hic fuga ex, voluptates vel eum ipsum amet, sunt corporis. Maxime odit alias, ratione tenetur, asperiores consequuntur deserunt modi velit ab maiores pariatur voluptates beatae aut nesciunt perspiciatis sed veritatis doloremque quibusdam amet vero. Qui, labore. Atque ratione quae ducimus reprehenderit perferendis nisi earum, debitis commodi maxime sequi facere optio doloribus, repudiandae ex quidem amet iusto inventore quaerat at praesentium sint. Omnis mollitia esse illum suscipit, quis dolorem maxime sunt eaque, autem nisi corrupti perferendis provident tempore quas, unde! Doloribus, at, accusamus, maiores enim amet quod provident temporibus atque, ipsam fugiat incidunt. Quasi iusto ea quibusdam eveniet porro officiis dicta fugiat fugit laudantium ipsum esse quisquam quo laboriosam odit voluptates alias veritatis expedita quidem consectetur eos, impedit, incidunt dolorum? Laborum, facere nulla ullam, aliquid rerum nihil non adipisci, architecto obcaecati iure quam, fuga minus alias eligendi provident ex odio sit. Ducimus, facilis veritatis numquam, maxime quos natus animi, a magnam itaque veniam pariatur sed alias eos quas? Voluptatum fugit doloribus fugiat iste adipisci quidem odit consectetur, sapiente culpa magnam laborum, laboriosam exercitationem cupiditate dignissimos, nisi doloremque hic itaque aspernatur. Ab labore dolorum cumque rem vitae repellat quo quae porro cupiditate minus. Perspiciatis cumque sequi provident fugit. Nulla reiciendis voluptates molestiae corporis voluptate, quidem consequuntur, dolor vero necessitatibus deleniti tempora ab facilis similique, ea error deserunt fuga quia atque omnis nam earum non, illo. Minima quos optio nostrum eos aperiam? Quam, obcaecati velit deserunt tempore, iure vitae repudiandae quos illum quasi esse quas quaerat at consectetur necessitatibus. Cum, quod, dolore voluptatibus quibusdam accusamus aliquam consequatur dolorum illo! Sequi commodi adipisci explicabo soluta necessitatibus magni expedita cumque, officiis voluptas, vel amet recusandae sunt, quidem eum aliquid deleniti unde, impedit non magnam consectetur est minima facere architecto. Molestias cum vero nostrum saepe, dignissimos eius beatae natus fugiat deserunt esse, nesciunt eos ducimus id amet magnam possimus? Optio adipisci quisquam earum totam nemo sunt provident iure ab consectetur et deleniti molestiae blanditiis laudantium, autem consequatur rerum labore ipsa ipsam deserunt nisi, expedita doloremque quibusdam! Illo nemo laborum a sequi in, ad ipsum blanditiis alias! Eaque eos eligendi hic dolorum sint, tempore voluptatum ut numquam. Corporis similique itaque accusantium, esse porro ea dolor, quae consequuntur ullam necessitatibus magni rem optio officiis totam in dicta quas, odio quam blanditiis dolores pariatur? Dolorem, fuga? Harum ratione nemo perspiciatis culpa eum repudiandae esse, atque impedit nihil debitis, assumenda est. Sapiente rerum alias ipsa tempore obcaecati deserunt maiores distinctio officiis itaque fugit optio, eveniet facere amet ipsum, harum laboriosam eius, enim magni blanditiis temporibus nobis consequuntur ut. Quia magnam vero atque modi aspernatur in perferendis voluptas reprehenderit, rerum dolore unde iusto ab non eius molestiae quasi tenetur beatae ipsam quidem, quos at architecto voluptate alias eos. Deserunt velit beatae, ullam, accusantium sit asperiores! A vero perferendis, harum praesentium dolorem deserunt. Numquam voluptas necessitatibus, aliquam ullam saepe harum amet consequatur minima neque officia maxime quo beatae ab aliquid ex placeat rerum unde, reiciendis aspernatur similique, doloremque ad laboriosam modi. Minus quam aperiam, sed aliquid. Fugiat amet harum consequuntur reprehenderit id eum ratione quos temporibus, quae. Ab ut omnis tempora voluptates, sed ea animi voluptatem pariatur quod mollitia corrupti voluptas repellendus consequatur quae adipisci, enim vitae harum nulla natus iusto hic totam officia architecto quam. Debitis dignissimos praesentium, hic. Ad assumenda, aliquid consequuntur dolore eum repudiandae ab explicabo ipsa sed blanditiis. Quidem unde necessitatibus facilis, quis commodi. Dignissimos perferendis, nihil labore corrupti autem cumque ipsum vel voluptatum? Nostrum labore, omnis provident ullam repellendus culpa amet rem consequatur animi, necessitatibus porro. In consequatur optio recusandae, quisquam accusantium at deserunt voluptatem fugit quibusdam neque libero assumenda consectetur numquam ratione quaerat. Quos omnis neque atque, id perferendis possimus, alias, dignissimos doloribus ducimus similique ratione vitae eos laudantium, tempore cupiditate quod consectetur! Voluptas enim laboriosam nesciunt rem. Recusandae beatae numquam asperiores adipisci neque, vel pariatur suscipit provident, a est magni. Laborum dolore incidunt saepe ipsam? Eveniet doloremque animi maxime aliquid rem fugit dolor dignissimos! Quo, ut quod ab.
              </main>
              <aside>
                  AD
              </aside>
          </section>
          <footer>
              <a href="https://opentutorials.org/course/1">홈페이지</a>
          </footer>
      </div>
  </body>
  </html>
  ```

## 출처

- [생활코딩 CSS 수업: media query](https://opentutorials.org/course/2418/13517)
